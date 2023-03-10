# SPy

Docker image for [spectral python (SPy)](http://www.spectralpython.net/). 

Uses SPy 0.23.1


## Docker

### Quick start

* Log into registry with the appropriate credentials:

  ```bash
  docker login -u public -p public public.aml-repo.cms.waikato.ac.nz:443 
  ```

* Pull and run image (adjust volume mappings `-v`):

  ```bash
  docker run \
    -v /local/dir:/container/dir \
    -it public.aml-repo.cms.waikato.ac.nz:443/wairas/happy-spy:0.23.1
  ```

* If need be, remove all containers and images from your system:

  ```bash
  docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q) && docker system prune -a
  ```

### Build local image

* Build the image from Docker file (from within `/path_to/0.23.1`)

  ```bash
  docker build -t spy .
  ```
  
* Run the container

  ```bash
  docker run \
    -v /local/dir:/container/dir -it spy
  ```
  `/local/dir:/container/dir` maps a local disk directory into a directory inside the container

### Pre-built images

* Build

  ```bash
  docker build -t happy-spy:0.23.1 .
  ```
  
* Tag

  ```bash
  docker tag \
    happy-spy:0.23.1 \
    public-push.aml-repo.cms.waikato.ac.nz:443/wairas/happy-spy:0.23.1
  ```
  
* Push

  ```bash
  docker push public-push.aml-repo.cms.waikato.ac.nz:443/wairas/happy-spy:0.23.1
  ```
  If error "no basic auth credentials" occurs, then run (enter username/password when prompted):
  
  ```bash
  docker login public-push.aml-repo.cms.waikato.ac.nz:443
  ```
  
* Pull

  If image is available in aml-repo and you just want to use it, you can pull using following command and then [run](#run).

  ```bash
  docker pull public.aml-repo.cms.waikato.ac.nz:443/wairas/happy-spy:0.23.1
  ```
  If error "no basic auth credentials" occurs, then run (enter username/password when prompted):
  
  ```bash
  docker login public.aml-repo.cms.waikato.ac.nz:443
  ```
  Then tag by running:
  
  ```bash
  docker tag \
    public.aml-repo.cms.waikato.ac.nz:443/wairas/happy-spy:0.23.1 \
    happy-spy:0.23.1
  ```
  
* <a name="run">Run</a>

  ```bash
  docker run \
    -v /local/dir:/container/dir -it happy-spy:0.23.1
  ```
  `/local/dir:/container/dir` maps a local disk directory into a directory inside the container


### Permissions

When running the docker container as regular use, you will want to set the correct
user and group on the files generated by the container (aka the user:group launching
the container):

```bash
docker run -u $(id -u):$(id -g) -e USER=$USER ...
```
