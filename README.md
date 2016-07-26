About AEM Solr Search Sample
=============================

This project is based on the AEM Solr Search that provides an example of intergration between AEM (CQ) and Apache Solr. It includes the following features:

* Quick start Solr distributions for development use
    * Apache Solr 4.10.4 - `aemsolrsearch-quickstart`
    * Apache Solr 5.4.1 - `aemsolrsearch-vagrant`

Requirements
------------

* Java 7 or greater
* Adobe AEM 6.1 or greater (with the Geometrixx Media Site)
* Maven 3.2.x


Getting Started
---------------

These instructions assume that AEM is running on localhost on port 4502 with the default admin/admin credentials.

1. Start AEM.

2. Clone and install the most recent ACS Commons Package [https://github.com/Adobe-Consulting-Services/acs-aem-commons](https://github.com/Adobe-Consulting-Services/acs-aem-commons)
   Referring : https://github.com/Adobe-Consulting-Services/acs-aem-commons
   
3. Clone, compile and install [AEM Solr Search 2.0.0](https://github.com/headwirecom/aem-solr-search) to AEM author.
      You may want to clone this project in another directory (i.e., outside of this project).
   
           $ git clone https://github.com/headwirecom/aem-solr-search.git
           $ cd aem-solr-search
           $ mvn clean install -Pauto-deploy-all   
           
4. Provision the demo Solr instance.
    
           $ cd <root path to this project>/solr-quickstart
           $ mvn clean resources:resources jetty:run
                     
   Or if you want to use the Vagrant, the follow:
   
           $ cd <root path to this project>/solr-vagrant
           $ vagrant up                 
    
5. Deploy the Geometrixx Media sample bundles. 

        $ mvn clean install -PautoInstallPackage
        $ mvn install -Pauto-deploy-geo
        $ mvn clean install -Pauto-deploy-sample
    
6. In another terminal window run the index script to perform a full index. Before running the following script, make sure to verify/update the CQ and Solr details. 

        $ cd geometrixx-media-sample
        $ ./index-geometrixx-media-articles.sh

7. Open a browser and visit:
    * Sample Geometrixx Media Search Page: [http://localhost:4502/cf#/content/aemsolrsearch/aem-solr-search-sample.html](http://localhost:4502/cf#/content/aemsolrsearch/aem-solr-search-sample.html)
    * Solr: [http://localhost:8888/solr/](http://localhost:8888/solr/)


For More Information
--------------------

Send an email to <pd@headwire.com>.
