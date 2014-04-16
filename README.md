MySqLiQuerryBuilder
===================

Examples:

1) Simple SELECT.

    $mysql = new simple_query_builder();
    $mysql->devMode = 1;                //Developer mode, if error it print your SQL query, Default is 0
    // $mysql->select returns assoc array, if result is 0 error, it returns false
    $res = $mysql->select("SELECT * FROM `sha1`", 0, 50);                       //0 - offset, 50 - limit
    if ($res)
    {
        echo $res[0]['pass'] ."<br>"; //Print 1 result, at first row.
        print_R($res); //Print array
    }
    
2) Simple INSERT.

    $mysql = new simple_query_builder();
    $mysql->devMode = 1;//Developer mode, if error it print your SQL query, Default is 0
    // $mysql->insert returns true if query is OK, and false if not OK
    $mysql->add('name','Ivan');//Add protected value from SQL Injections.
    $mysql->add('address',$_POST['address']);//Add protected value from SQL Injections.
    $mysql->addCustom('activeTime', 'NOW() + INTERVAL 1 DAY'); //Add non protected value, good for MySQL fucntions
    $res = $mysql->insert('users'); //Insert into table `users`
    if ($res) echo 'ok'; else echo 'not ok';
    
3) Simple UPDATE.

    $mysql = new simple_query_builder();
    $mysql->devMode = 1;//Developer mode, if error it print your SQL query, Default is 0
    // $mysql->insert returns true if query is OK, and false if not OK 
    $mysql->add('name','Ivan');//Add protected value from SQL Injections.
    $mysql->add('address',$_POST['address']);//Add protected value from SQL Injections.
    $mysql->addCustom('activeTime', 'NOW() + INTERVAL 1 DAY'); //Add non protected value, good for MySQL fucntions
    $res = $mysql->update('users'); //Update all `users`
    $res2 = $mysql->update('users',"id = 458, AND name = 'Viktor'"); //Update user in `users`, where ...
    if ($res) echo 'ok 1'; else echo 'not ok 1';
    if ($res2) echo 'ok 2'; else echo 'not ok 2';
