Cobbled together from [http://www.mediawiki.org/wiki/Manual:Tag_extensions Manual:Tag_extensions ]:

<syntaxhighlight lang="php">
 <?php
/**
 * CompaTables - this extension adds a browser compatability table to articles based on arguments
 *
 * To activate this extension, add the following into your LocalSettings.php file:
 * require_once('$IP/extensions/CompaTables/compatables.php');
 *
 * @ingroup Extensions
 * @author Doug Schepers <schepers@w3.org>
 * @version 1.0
 * @link https://www.mediawiki.org/wiki/Extension:CompaTables Documentation
 * @license http://www.gnu.org/copyleft/gpl.html GNU General Public License 2.0 or later
 */
 
/**
 * Protect against register_globals vulnerabilities.
 * This line must be present before any global variable is referenced.
 */
if( !defined( 'MEDIAWIKI' ) ) {
        echo( "This is an extension to the MediaWiki package and cannot be run standalone.\n" );
        die( -1 );
}
 
// Extension credits that will show up on Special:Version    
$wgExtensionCredits['validextensionclass'][] = array(
        'path'           => __FILE__,
        'name'           => 'CompaTables',
        'version'        => '1.0',
        'author'         => 'Doug Schepers', 
        'url'            => 'https://www.mediawiki.org/wiki/Extension:CompaTables',
        'descriptionmsg' => 'compatablesmessage',
        'description'    => 'Adds browser compatability table to article based on arguments'
);
 
$wgHooks['ParserFirstCallInit'][] = 'compaTablesSetup';
 
function compaTablesSetup( Parser $parser ) {
        $parser->setHook( 'compatibility', 'compaTablesOut' );
        return true;
}

/* The following lines can be used to get the variable values directly:
        $to = $args['to'] ;
        $email = $args['email'] ;
*/
function compaTablesOut( $text, array $args, Parser $parser, PPFrame $frame ) {
        $output = $parser->recursiveTagParse( $text, $frame );
        // return '<table class="wonderful"><tr><th>' . $output . '</th><td>' . $args['feature'] . '</td></tr></table>';
        return '<table class="wonderful"><tr><th>' . $output . '</th></tr></table>';
}
</syntaxhighlight>