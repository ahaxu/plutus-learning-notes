FROM ubuntu:16.04

WORKDIR /home/installer/src

COPY . /home/installer/src

RUN \
    apt update && \
    apt upgrade && \
    apt-get install gzip && \
    apt-get install xz-utils && \
    apt-get install gnupg2 -y && \
    apt install curl -y && \
    apt install make && \
    apt-get install vim -y && \
    apt-get install sudo && \
    apt install git -y

RUN \
    groupadd -g 999 installer && useradd -u 999 -g installer -G sudo -m -s /bin/bash installer && \
    sed -i /etc/sudoers -re 's/^%sudo.*/%sudo ALL=(ALL:ALL) NOPASSWD: ALL/g' && \
    sed -i /etc/sudoers -re 's/^root.*/root ALL=(ALL:ALL) NOPASSWD: ALL/g' && \
    sed -i /etc/sudoers -re 's/^#includedir.*/## **Removed the include directive** ##"/g' && \
    echo "installer ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers && \
    echo "Customized the sudoers file for passwordless access to the installer user!" && \
    echo "installer user:";  su - installer -c id

RUN mkdir -m 0755 /nix && chown installer:installer /nix && \
    chown installer:installer /home/installer

USER installer

ENV USER="installer"

RUN touch ~/.bashrc && \
    echo ". /home/installer/.nix-profile/etc/profile.d/nix.sh" >> ~/.bashrc

CMD ["/bin/bash", "startup.sh"]