# GeoMapas



Instalacion Geonode con docker https://docs.geonode.org/en/2.8/tutorials/install_and_admin/running_docker/setup_docker.html

docker-compose.override.localhost.yml
version: '2.2'
services:

  django:
    build: .
    # Loading the app is defined here to allow for
    # autoreload on changes it is mounted on top of the
    # old copy that docker added when creating the image
    volumes:
      - '.:/usr/src/app'
    environment:
      - DEBUG=False
      - GEONODE_LB_HOST_IP=52.140.240.41
      - GEONODE_LB_PORT=80
      - SITEURL=http://52.140.240.41/
      - ALLOWED_HOSTS=['localhost', '*']
      - GEOSERVER_PUBLIC_LOCATION=http://52.140.240.41/geoserver/
      - GEOSERVER_WEB_UI_LOCATION=http://52.140.240.41/geoserver/

  geoserver:
    environment:
      - GEONODE_LB_HOST_IP=52.140.240.41
      - GEONODE_LB_PORT=80

 
