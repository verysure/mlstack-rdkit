BootStrap: docker
From: ubuntu:bionic

%labels
    MAINTAINER verysure

%files
    env.yml /


%post
    apt-get -qq update --fix-missing 
    apt-get install -yq wget tar gzip bzip2 libxrender-dev libxext-dev

    # install conda
    wget --quiet https://repo.continuum.io/miniconda/Miniconda3-4.4.10-Linux-x86_64.sh -O /tmp/miniconda.sh
    bash /tmp/miniconda.sh -b -p /opt/conda
    rm /tmp/miniconda.sh

    # install packages in conda
    . /opt/conda/etc/profile.d/conda.sh
    /opt/conda/bin/conda config --set auto_update_conda False
    /opt/conda/bin/conda env update -n base --file=/env.yml

    # clean up
    conda clean -y -a
    apt-get clean -yq

%environment
export PATH=/opt/conda/bin:$PATH



