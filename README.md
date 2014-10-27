# hydra-jetty

This is a copy of jetty with the needed applications for running Hydra.  These include two java-based applications:

* [Fedora repository](https://github.com/futures/fcrepo4)
* [Solr](http://lucene.apache.org/solr/)

## Included Versions

* jetty: 8.1.10.v20130312
* solr: 4.9.0
* fedora: 4.0.0b2

## Usage

### Dependencies

* [Java 7 (JRE)](https://java.com/en/download/index.jsp)

### Manual

    git clone https://github.com/projecthydra/hydra-jetty
    cd hydra-jetty
    java -Xmx256m -XX:MaxPermSize=256m -jar start.jar

You can also change the port jetty starts on by editing the file etc/jetty.xml and changing this line to indicate a different port number:

    <Set name="port"><SystemProperty name="jetty.port" default="8983"/></Set>

### Using jettywrapper

For use within your Hydra application's Rails directory.

    rake jetty:install
    rake jetty:start

See [jettywrapper](https://github.com/projecthydra/jettywrapper) for more information regarding configuration and usage.
Port numbers and other java options maybe configured via the gem.

### Interaction

When jetty is finished initializing itself, Solr is available at

* [http://localhost:8983/solr/](http://localhost:8983/solr/)

and Fedora is available at

* [http://localhost:8983/fedora/](http://localhost:8983/fedora/)

You can see a list of all installed applications at

* [http://localhost:8983](http://localhost:8983)

### Updating

#### Solr and Jetty

Solr is updated by downloading the latest from [Lucene](http://lucene.apache.org/solr/), which includes an instance of Jetty in the
`example` directory.  Updating is a process of replacing the jar files as well as the solr.war and start.jar files.  Note that the
example from Lucene does not include the start.ini file.

#### Fedora4

If you want a bleeding edge version of fedora4, you can:
* Clone the [fcrepo4 git repository](https://github.com/fcrepo4/fcrepo4).
* Follow its build instructions in the `README to build the war project
* Copy the new warfile from `{your_local_fcrepo4_dir}/fcrepot-webapp/target/fcrepo-webapp-4.0.0-beta-04-SNAPSHOT.war` to `{your_local_hydra_jetty_dir}/webapps`
* Commit the project, then push to github
