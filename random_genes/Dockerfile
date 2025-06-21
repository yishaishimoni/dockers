FROM rocker/rstudio:latest

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libxt-dev \
    libxml2-dev \
    libssl-dev \
    libcurl4-openssl-dev \
    libpng-dev \
    libjpeg-dev \
    libtiff-dev \
    git \
    fonts-dejavu \
    && rm -rf /var/lib/apt/lists/*

# Install CRAN packages
RUN R -e "install.packages(c('amap', 'progress', 'gplots', 'extrafont', 'remotes', 'BiocManager'), repos='https://cloud.r-project.org')"

# Install Bioconductor package
RUN R -e "BiocManager::install('TCGAbiolinks')"

# Install phenoClust from GitHub
RUN R -e "remotes::install_github('yishaishimoni/phenoClust')"

# Clone Random_Genes repository and set permissions
RUN git clone https://github.com/yishaishimoni/Random_Genes.git /home/rstudio/Random_Genes && chown -R rstudio:rstudio /home/rstudio/Random_Genes
