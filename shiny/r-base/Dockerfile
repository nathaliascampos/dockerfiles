FROM openanalytics/r-base:3.6.1

# update system libraries
RUN apt-get update && apt-get upgrade -y

# system libraries 
# Try to only install system libraries you actually need
# Package Manager is a good resource to help discover system deps
RUN apt-get update && apt-get install -y \
    sudo \
    pandoc \
    pandoc-citeproc \
    libcurl4-gnutls-dev \
    libcairo2-dev \
    libxt-dev \
    libssh2-1-dev \
    libssl1.0.0

# install R packages required 
RUN R -e "install.packages(c('shiny'), repos='https://cloud.r-project.org/')"

# copy the app to the image
RUN mkdir /root/dash-shiny
COPY dash-shiny /root/dash-shiny

COPY Rprofile.site /usr/lib/R/etc/

EXPOSE 3838

CMD ["R", "-e", "shiny::runApp('/root/dash-shiny')"]
