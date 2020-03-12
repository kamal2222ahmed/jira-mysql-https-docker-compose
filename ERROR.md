mysql          | 2020-02-26T08:50:59.694583Z 2 [Note] Access denied for user 'JIRA_MYSQL_USER'@'172.26.0.4' (using password: YES)

resolution:

GRANT ALL PRIVILEGES ON root.* TO 'your_db'@'172.21.0.1' IDENTIFIED BY 'Password';

- MYSQL_ROOT_PASSWORD=supersecret
      - MYSQL_DATABASE=jiradb          # this database will be created on image startup
      - MYSQL_USER=jiradbuser               # this user will be granted superuser permissions on MYSQL_DATABASE
      - MYSQL_PASSWORD=12345

GRANT ALL PRIVILEGES ON *.* TO 'jiradb'@'172.21.0.1' IDENTIFIED BY 'supersecret';
FLUSH PRIVILEGES;


Quextion is how ot run these commands inside a docker-compose file

28-Feb-2020 14:55:44.017 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-8080"]
jira           | 28-Feb-2020 14:55:44.041 INFO [main] org.apache.tomcat.util.net.NioSelectorPool.getSharedSelector Using a shared selector for servlet write/read
jira           | 28-Feb-2020 14:55:44.067 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in 5285 ms
jira           | 2020-02-28 14:55:44,174 JIRA-Bootstrap INFO      [c.a.j.config.database.SystemDatabaseConfigurationLoader] Reading database configuration from /var/atlassian/jira/dbconfig.xml
jira           | 2020-02-28 14:55:44,543 JIRA-Bootstrap ERROR      [c.a.config.bootstrap.DefaultAtlassianBootstrapManager] Could not successfully test your database:
jira           | com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure
jira           |
jira           | The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
jira           | 	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
jira           | 	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
jira           | 	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
jira           | 	at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
jira           | 	at com.mysql.jdbc.Util.handleNewInstance(Util.java:404)
jira           | 	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:981)
jira           | 	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:339)
jira           | 	at com.mysql.jdbc.ConnectionImpl.coreConnect(ConnectionImpl.java:2253)
jira           | 	at com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2286)
jira           | 	at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2085)
jira           | 	at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:795)
jira           | 	at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:44)
jira           | 	... 3 filtered
jira           | 	at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
jira           | 	at com.mysql.jdbc.Util.handleNewInstance(Util.java:404)
jira           | 	at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:400)
jira           | 	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:327)
jira           | 	at java.sql.DriverManager.getConnection(DriverManager.java:664)
jira           | 	at java.sql.DriverManager.getConnection(DriverManager.java:247)
jira           | 	at com.atlassian.config.bootstrap.DefaultAtlassianBootstrapManager.getTestDatabaseConnection(DefaultAtlassianBootstrapManager.java:347)
jira           | 	at com.atlassian.jira.config.database.JdbcDatasource.getConnection(JdbcDatasource.java:211)
jira           | 	at com.atlassian.jira.config.database.DatabaseConfig.testConnection(DatabaseConfig.java:88)
jira           | 	at com.atlassian.jira.health.checks.DbConfigurationAndConnectionCheck.doPerform(DbConfigurationAndConnectionCheck.java:60)
jira           | 	at com.atlassian.jira.health.HealthCheckTemplate.perform(HealthCheckTemplate.java:23)
jira           | 	at com.atlassian.jira.health.DefaultHealthCheckExecutor.runCheck(DefaultHealthCheckExecutor.java:74)
jira           | 	at com.atlassian.jira.health.DefaultHealthCheckExecutor.lambda$applyAndCollectExceptions$1(DefaultHealthCheckExecutor.java:53)
jira           | 	at java.util.stream.ForEachOps$ForEachOp$OfRef.accept(ForEachOps.java:184)
jira           | 	at java.util.stream.ReferencePipeline$2$1.accept(ReferencePipeline.java:175)
jira           | 	at java.util.Iterator.forEachRemaining(Iterator.java:116)
jira           | 	at java.util.Spliterators$IteratorSpliterator.forEachRemaining(Spliterators.java:1801)
jira           | 	at java.util.stream.AbstractPipeline.copyInto(AbstractPipeline.java:481)
jira           | 	at java.util.stream.AbstractPipeline.wrapAndCopyInto(AbstractPipeline.java:471)
jira           | 	at java.util.stream.ForEachOps$ForEachOp.evaluateSequential(ForEachOps.java:151)
jira           | 	at java.util.stream.ForEachOps$ForEachOp$OfRef.evaluateSequential(ForEachOps.java:174)
jira           | 	at java.util.stream.AbstractPipeline.evaluate(AbstractPipeline.java:234)
jira           | 	at java.util.stream.ReferencePipeline.forEach(ReferencePipeline.java:418)
jira           | 	at com.atlassian.jira.health.DefaultHealthCheckExecutor.applyAndCollectExceptions(DefaultHealthCheckExecutor.java:53)
jira           | 	at com.atlassian.jira.health.DefaultHealthCheckExecutor.performHealthChecks(DefaultHealthCheckExecutor.java:42)
jira           | 	at com.atlassian.jira.health.HealthChecks.executeChecksAndRecordResults(HealthChecks.java:164)
jira           | 	at com.atlassian.jira.health.HealthChecks.runHealthChecks(HealthChecks.java:154)
jira           | 	at com.atlassian.jira.health.HealthChecks.runHealthChecks(HealthChecks.java:66)
jira           | 	at com.atlassian.jira.startup.BootstrapContainerLauncher.start(BootstrapContainerLauncher.java:48)
jira           | 	at com.atlassian.jira.startup.DefaultJiraLauncher.preDbLaunch(DefaultJiraLauncher.java:115)
jira           | 	at com.atlassian.jira.startup.DefaultJiraLauncher.lambda$start$0(DefaultJiraLauncher.java:101)
jira           | 	at com.atlassian.jira.util.devspeed.JiraDevSpeedTimer.run(JiraDevSpeedTimer.java:31)
jira           | 	at com.atlassian.jira.startup.DefaultJiraLauncher.start(DefaultJiraLauncher.java:100)
jira           | 	at com.atlassian.jira.startup.LauncherContextListener.initSlowStuff(LauncherContextListener.java:154)
jira           | 	at java.lang.Thread.run(Thread.java:748)
jira           | Caused by: java.net.ConnectException: Connection refused (Connection refused)
jira           | 	at java.net.PlainSocketImpl.socketConnect(Native Method)
jira           | 	at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:350)
jira           | 	at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
jira           | 	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
jira           | 	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
jira           | 	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:211)
jira           | 	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:298)
jira           | 	... 43 more
jira           | 2020-02-28 14:55:44,583 JIRA-Bootstrap ERROR      [c.a.jira.health.HealthChecks] JIRA couldn't connect to your database
jira           | 2020-02-28 14:55:44,585 JIRA-Bootstrap ERROR      [c.a.jira.health.HealthChecks] JIRA failed to establish a connection to your database.
jira           |     This could be because:
jira           |     	- Your database isn't running
jira           |     	- The configuration of your dbconfig.xml file is incorrect (user, password, or database URL etc.)
jira           |     	- There is a network issue between JIRA and your database (e.g. firewall, database doesn't allow remote access etc.)
jira           |
jira           |     There are several other solutions you can try, review our documentation and see what works for you.
jira           |
jira           | 2020-02-28 14:55:44,589 JIRA-Bootstrap INFO      [c.a.jira.startup.JiraStartupLogger] Running JIRA startup checks.
jira           | 2020-02-28 14:55:44,590 JIRA-Bootstrap FATAL      [c.a.jira.startup.JiraStartupLogger] Startup check failed. JIRA will be locked.
jira           | 2020-02-28 14:55:44,761 JIRA-Bootstrap INFO      [c.a.jira.startup.LauncherContextListener] Memory Usage:
jira           |     ---------------------------------------------------------------------------------
jira           |       Heap memory     :  Used:   33 MiB.  Committed:  484 MiB.  Max:  740 MiB
jira           |       Non-heap memory :  Used:   42 MiB.  Committed:   65 MiB.  Max: 1536 MiB
jira           |     ---------------------------------------------------------------------------------
jira           |       TOTAL           :  Used:   75 MiB.  Committed:  549 MiB.  Max: 2276 MiB
jira           |     ---------------------------------------------------------------------------------

Fixed, by using 

environment:
      ## Use % to allow remote access to all addresses. 
      ## Generally not recommended by some people to allow for root.
      #- MYSQL_ROOT_HOST=% 

      # This allows ip ranges from 192.168.0.49 to 192.168.0.54 to connect to root
      - MYSQL_ROOT_HOST=192.168.0.48/255.255.255.248

=====================================================
00:17 $ docker-compose ps
WARNING: Some services (jira) use the 'deploy' key, which will be ignored. Compose does not support 'deploy' configuration - use `docker stack deploy` to deploy to a swarm.
   Name                  Command               State                     Ports
------------------------------------------------------------------------------------------------
jira          /docker-entrypoint.sh /opt ...   Up       0.0.0.0:8080->8080/tcp
letsencrypt   /bin/bash /app/entrypoint. ...   Exit 1
mysql         docker-entrypoint.sh mysqld      Up       3306/tcp, 33060/tcp
nginx-proxy   /app/docker-entrypoint.sh  ...   Up       0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
(base) ✔ ~/QA/TIGERTEAM/PROJECT-DASHBOARDS/jira-mysql-https-docker-compose [master|✚ 3…5]
00:17 $ docker-compose logs | grep letsencrypt
WARNING: Some services (jira) use the 'deploy' key, which will be ignored. Compose does not support 'deploy' configuration - use `docker stack deploy` to deploy to a swarm.
Attaching to jira, letsencrypt, mysql, nginx-proxy
letsencrypt    | Error: you need to share your Docker host socket with a volume at /var/run/docker.sock
letsencrypt    | Typically you should run your container with: '-v /var/run/docker.sock:/var/run/docker.sock:ro'


