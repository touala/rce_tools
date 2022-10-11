Bootstrap: docker
From: centos:centos8

%help
For more information, please consult https://github.com/touala/rce_tools

# Add files to the container
%setup
    cp postInstall /tmp/postInstall

# Install dependencies
%post
    # Install basic dependencies
    dnf upgrade -y
    dnf group install -y "Development Tools"
    dnf install -y python3-devel
    dnf install -y zlib-devel

    # Define working directory
    mkdir /home/rce_tools
    cd /home/rce_tools

    # Install remaining dependencies
    mv /tmp/postInstall /postInstall
    bash /postInstall

    # Set default behavior
    cat > /.singularity.d/env/99-custom.sh <<EOF
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]rce_tools:\[\033[33;1m\]\w\[\033[m\]$ "
SINGULARITY_SHELL=/bin/bash
EOF

%environment
    export HOME=/home/rce_tools

%runscript
    cd /home/centos8
    exec /bin/bash
