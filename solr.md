mkdir -p /var/solr/data/detail_table

cp -r /opt/solr/server/solr/configsets/_default/conf /var/solr/data/detail_table/



mkdir data



docker exec -it --user root solr bash

chown -R solr:solr /var/solr/data/detail_table