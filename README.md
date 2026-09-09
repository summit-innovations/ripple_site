# Ripple Site Project

This repository contains the files and configurations for the ripple_site and APIs. 

## Pipeline

The nginx service uses an nginx config file in `/etc/nginx/sites-available` called `nginx-config`. That file used to be housed on this repo, but it is managed by CertBot and other services within Linux, so I returned it to its original location. To facilitate easy feature development and debugging, I abstracted away the endpoints and put them in this github repo. These endpoints define the different ways the API can be accessed. There are two primary branches: development and production. The production branch forwards all requests to those endpoints to the `audio-uploader-prod.service` running on port 8000. The development branch looks identical to the production branch except it adds the extension `/dev` to each related endpoint. It forwards requests to those endpoints to the `audio-uploader-dev.service` running on port 8080. The link between `endpoints.conf` and `nginx-config` is an include statement that I manually added to `nginx-config`. If needed, you can remove/edit it there. This new pipeline should allow us to easily expose new endpoints and add software features more easily. 

## Changelog

- 7/27/26: Created repository. I hope to add the other HTML and CSS files to this project as necessary. This will also contain the API configurations that ripple_server will use. 
- 7/28/26: Moved HTML file and server config into the git repository. The config should be symlinked to the actual config but we can edit it here. Same with the HTML file. 
- 9/8/26: Changed server config file and abstracted away endpoints for easy development
- 9/8/26: Updated index html page. When queried using `?env=dev`, the site will show results from the dev service. 

