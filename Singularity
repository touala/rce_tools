Bootstrap: docker
From: centos:centos8

%help
For more information, please consult https://github.com/touala/rce_tools

# Install dependencies
%post
    # Install basic dependencies
    dnf upgrade -y
    dnf group install -y "Development Tools"
    dnf install -y python3-devel
    dnf install -y zlib-devel
    dnf install -y git-all

    git clone https://github.com/touala/rce_tools
    bash rce_tools/postInstall

    # Define working directory
    mkdir /home/rce_tools
    cd /home/rce_tools

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
