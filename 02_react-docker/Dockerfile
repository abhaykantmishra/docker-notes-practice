FROM node:20-alpine

# Create a user with permissions to run the app
# -S -> creates a system user
# -G -> Add the user to a group
# This is done to avoid running the app as as root
# if the app is running as a root, any vulnerability in the app can be exploited to gain access to the host system.
# Good practice to run a app as a non-root user
RUN addgroup app && adduser -S app -G app

# Set the user to run the app
USER app

# Set the working dir to /app
WORKDIR /app

# Copy the package.json and package.lock.json to working directory
# This is done to gain the advantage of docker cache before copying other files
# If both these files are not changed, Docker will use cached deps
COPY package*.josn ./

# Sometime the ownership of files in working dir is changed to root thus app can not access them
# To avoid this err change ownership of files to root the root user
USER root

# Change the ownership of the /app to the app user
# chown <user>:<group> <directory>
RUN chown app:app .

# Install deps
RUN npm install

# Copy rest of the files
COPY . .

# Expose a port to run the container on that port
EXPOSE 5173

# Run the app in development mode:
CMD npm run dev

