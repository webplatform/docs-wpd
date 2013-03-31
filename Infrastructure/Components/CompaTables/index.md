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
 
$wgExtensionFunctions[] = 'CompaTables';

// Extension credits that will show up on Special:Version    
$wgExtensionCredits['parserHook'][] = array(
        'name'           => 'CompaTables',
        'version'        => '1.0',
        'author'         => 'Doug Schepers', 
        'url'            => 'https://www.mediawiki.org/wiki/Extension:CompaTables',
        'descriptionmsg' => 'compatablesmessage',
        'description'    => 'Adds browser compatability table to article based on arguments'
);
 
 
function CompaTables() {
  global $wgParser;
  $wgParser->setHook('compatability', 'renderCompaTables');
}

function renderCompaTables($input, array $args) {
    // jSON URL which should be requested
    $json_url = 'http://docs.webplatform.org/compat/data.json';
     
    // jSON String for request
    $json_string = 'border-image';
     
    // Initializing curl
    $ch = curl_init( $json_url );
     
    // Configuring curl options
    $options = array(
        CURLOPT_RETURNTRANSFER => true,
        CURLOPT_HTTPHEADER => array('Content-type: application/json') ,
        CURLOPT_POSTFIELDS => $json_string
    );

    // Setting curl options
    curl_setopt_array( $ch, $options );
     
   // Getting results
    $string =  curl_exec($ch); // Getting jSON result string
    curl_close($ch);
    $result = json_decode($string, true);


    // extracting data for feature
    $feature = $result['data'][ $args['feature'] ];
    $stats = $feature['stats'];

    // initialize information for both tables
    $tables = array( 
        array(
            'title' => 'Desktop',
            'thead' => '<thead><tr><th>Feature</th><th>Chrome</th><th>Firefox</th><th>Internet Explorer</th><th>Opera</th><th>Safari</th></tr></thead>',
            'uas' => array('chrome', 'firefox', 'ie', 'opera', 'safari')
        ),
        array(
            'title' => 'Mobile',
            'thead' => '<thead><tr><th>Feature</th><th>Android</th><th>BlackBerry</th><th>Chrome for mobile</th><th>Firefox Mobile</th><th>IE Mobile</th><th>Opera Mobile</th><th>Opera Mini</th><th>Safari Mobile</th></tr></thead>',
            'uas' => array('android', 'bb', 'and_chr', 'and_ff', 'ie_mob', 'op_mob', 'op_mini', 'ios_saf')
        )
    );

    $prefixes = array(
        'chrome' => 'webkit',
        'safari' => 'webkit',
        'android' => 'webkit',
        'and_chr' => 'webkit',
        'ios_saf' => 'webkit',
        'bb' => 'webkit',
        'firefox' => 'moz',
        'ie' => 'ms',
        'ie_mob' => 'ms',
        'firefox' => 'moz',
        'and_ff' => 'moz',
        'firefox' => 'moz',
        'opera' => 'o',
        'op_mob' => 'o',
        'op_mini' => 'o'
    );

    // format tables for desktops and mobiles
    $out = '';
    $trace = 'Trace: ';
    foreach ($tables as $table) {
        $out .= '<h3>' . $table['title'] . '</h3>';
        $out .= '<table class="compat-table">';
        $out .= $table['thead'];
        $out .= '<tbody><tr><td>Basic Support</td>';

        $uas = $table['uas'];
            $trace.='<p>' . implode(', ', $uas) . '</p>';


        foreach ($uas as $ua) {
            $support = 'unsupported';

            $versions = $stats[ $ua ];
            if ($versions) {
                $newvalue = '';
                $supporthistory = '';
                foreach ($versions as $v => $value) {
                    if ($newvalue != $value) {
                        $newvalue = $value;
                        switch ($value) {
                            case 'a':
                                $supporthistory .= '<div>' . $v . ' <span class="partial-support">partial</span></div>';
                                continue; 
                            case 'a x':
                                $supporthistory .= '<div>' . $v . ' <span class="partial-support">partial</span><span class="prefix ' . $prefixes[$ua] . '">-' . $prefixes[$ua] . '</span></div>';
                                continue; 
                            case 'y x':
                                $supporthistory .= '<div>' . $v . ' <span class="prefix ' . $prefixes[$ua] . '">-' . $prefixes[$ua] . '</span></div>';
                                continue; 
                            case 'y':
                                $supporthistory .= '<div>' . $v . '</div>';
                                break;
                            case 'p':
                                $supporthistory .= '<div>' . $v . ' <i>unsupported, polyfill available</i></div>';
                                continue; 
                            case 'u':
                                $supporthistory .= '<div>' . $v . ' <i>?</i></div>';
                                continue; 
                            case 'u p':
                                $supporthistory .= '<div>' . $v . ' <i>?, polyfill available</i></div>';
                                continue; 
                        }
                    }
                }
                $support = $supporthistory;
                $newvalue = '';
            } else {
                $support = '?';
            }
            $out.='<td>' . $support . '</td>';
        }

        $out.='</tr></tbody></table>';
    }
    // $out .= $trace;

    return $out;
}            
</syntaxhighlight>