Please keep in mind this is an old script I wrote many many years ago, as you can see from where it is forked from. No need to redo whats not broken, or search for something better. At least right now theres no need to. I have done a few changes to bring it up to todays standards some.

##PHP's simple Minify
Compressing and minifying your css and javascript files on the fly.
This class will update the compressed css or javascript file when a change has been made to one the files being included.
It will also add `?vers=` to the url with the last time the file was compressed at the end of the string.

Please help improve the JS minify function

###Simple to use,

````php
/* example
*
*	@type = css || js
*	@files = array of the files to compress
*	@file = the /path/to/savedFile.css of the file
*
*	function compress($type, $files, $file)
*
*	// the numbers is the filemtime() of the cache file
*	@return '/path/to/savedFile.css?vers=987589745';
*/
use JW3B\core;

// to compress css files
$CSSFiles = [
	'/style/css/fonts/Lilly-fontfacekit/stylesheet.css',
	'/style/css/bootstrap.css',
	'/style/css/bs_extended.css'
];
$min = new Minify;
$CSSFile = $min->compress('css', $CSSFiles, '/assets/compressedFiles/css.global.min.css');

// to compress javascript files
$JSFiles = [
	'/style/js/bootstrap.min.js',
	'/style/js/jquery.form.js',
	'/style/js/global.js'
];

$JSFile = $min->compress('js', $JSFiles, '/assets/compressedFiles/js.global.min.js');

// and then eco it out
echo '<link type="text/css" rel="stylesheet" href="'.$CSSFile.'">'.
	'<script type="text/javascript" src="'.$JSFile.'"></script>';
````
