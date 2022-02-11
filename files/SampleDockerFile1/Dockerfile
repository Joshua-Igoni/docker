#Docker Base image 
FROM nginx:1.21.3

#Maintainer
MAINTAINER Bikram <bikramatmedium@gmail.com>

#Set the working directory
WORKDIR /app 

#Create a test directory 
RUN mkdir /app/test-folder

#Download the sameple tar file and place in test directory
ADD https://github.com/samtools/samtools/releases/download/1.2/samtools-1.2.tar.bz2 /app/test-folder/

#Download the sample index.html file and place in test directory
ADD https://www.google.com/index.html /app/test-folder

#Copy the index.html file to this path - /usr/share/nginx/html/
COPY index.html /usr/share/nginx/html/

# Copy the folder to /tmp
COPY folder1   /app/test-folder/

#Set ENV veriable for Nginx 
ENV My_Nginx_version 1.21.3

#Expose the port that nginx will listen 
EXPOSE 80

# Create A Volume 
VOLUME /data

#Check health_check 
HEALTHCHECK --interval=5s --timeout=3s  --start-period=30s CMD curl --fail http://localhost || exit 1 

# Start the Ngnix service 
CMD ["nginx", "-g", "daemon off;"]

