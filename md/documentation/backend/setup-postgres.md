# Using servlet with PostgreSQL

1. Install PostgreSQL: http://www.postgresql.org/ (tested with version 9.3)

2. create a database with name `oskaridb` and change the database connection parameters:

    For quick testing you can modify the values in `oskari-server/servlet-map/filter/filter-base.properties`

        db.jndi.driverClassName=org.hsqldb.jdbcDriver
        db.url=jdbc:hsqldb:file:data/oskaridb
        db.username=
        db.password=

    Or you can setup your maven profile settings to override the defaults like instructed in [customizing property values](/documentation/backend/customize-properties)

3. Start the server with `mvn clean install -f servlet-map-pom.xml -Doskari.dropdb=true -Doskari.setup=postgres-default -Pjetty-profile`

4. Open your browser with http://localhost:2373/?viewId=2 to see a new view loaded from the database.

    You should now see personaldata and publisher bundles started compared to the default view.
    Note in some environments the `jettyEnvXml` needs to be specified in `oskari-server/servlet-map/pom.xml` to be able to connect to the database. If the connection fails, enable `jettyEnvXml` in `pom.xml` and try again.

5. Adding [admin bundles for admin role](/documentation/backend/adding-bundles)