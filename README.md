Docker builds for various Astronomical software packages
========================================================

Docker builds for software packages that are used in e-MERLIN. These docker builds
are also intended as the basis of singularity builds.

The deb directory contains a debian build environment and the rhe directory a 
Red Hat/Centos build environment.

The casa6_conda directory contains a debian build environment with a conda installation
of the casa software. 

Some attempts at optimization, e.g. multi-stage builds to remove unnecessary 
packages in the final image, are made to reduce the final image size. In addition
some attempt at modularising the functionality is made so that it is obvious what the 
particular minimum dependencies are for the deployment of the target software.

In general if you are building locally then you should use the name in the docker
label metadata registry key e.g.


    docker build -t jbo/astrobuild-rhe rhe/buildbase/
 
so that the inheritance relationships between the images work.
 
    
 Development tips
 ----------------
    
* to look at image sizes https://github.com/wagoodman/dive
* failed builds https://stackoverflow.com/questions/26220957/how-can-i-inspect-the-file-system-of-a-failed-docker-build?rq=1 - in particular the following is necessary for
newer dockers as the buildkit gets in the way of seeing images.
   
    DOCKER_BUILDKIT=0 docker build ... 
