== Summary ==
Collection of small shell scripts that will be used to test components of the infrastructure.

== By technology ==
=== PHP Memcache library connection to Memcache cluster ===

    $params = array(
             'class'      => 'MemcachedPeclBagOStuff',
             'serializer' => 'php',
             'servers'    => array(
                     '10.1.1.1:11211',
                     '10.2.2.2:11211',
             ),
             'timeout' => 250000,
             'connect_timeout' => 300
    );

    $client = new Memcached;
    $client->setOption( Memcached::OPT_CONNECT_TIMEOUT, $params['connect_timeout'] * 1000 );
    $client->setOption( Memcached::OPT_SEND_TIMEOUT, $params['timeout'] );
    $client->setOption( Memcached::OPT_RECV_TIMEOUT, $params['timeout'] );
    $client->setOption( Memcached::OPT_POLL_TIMEOUT, $params['timeout'] / 1000 );
    $client->setOption( Memcached::OPT_LIBKETAMA_COMPATIBLE, true );
    $client->setOption( Memcached::OPT_SERIALIZER, Memcached::SERIALIZER_PHP );

    //require('/srv/webplatform/wiki/current/includes/GlobalFunctions.php');
    require('/srv/webplatform/wiki/current/includes/IP.php');
    //require('/srv/webplatform/wiki/current/includes/objectcache/MemcachedPeclBagOStuff.php');

    $servers = array();
    foreach ( $params['servers'] as $host ) {
        $servers[] = IP::splitHostAndPort( $host ); // (ip, port)
    }
    $client->addServers( $servers );

    $tmp_object = new stdClass;
    $tmp_object->str_attr = 'test';
    $tmp_object->int_attr = 123;
    $tmp_object->date = new DateTime();

    $client->add('key1', $tmp_object, 10) or die ("Failed to save data at the server");

    var_dump($client->get('key1'));
    var_dump($client->get('wpwiki:user:stats:359'));