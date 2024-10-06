# Step 1: Use an official lightweight NGINX image
FROM nginx:alpine

# Step 2: Set the working directory
WORKDIR /usr/share/nginx/html

# Step 3: Copy the static files into the container
COPY .. /usr/share/nginx/html

# Step 4: Expose the port that NGINX will run on
EXPOSE 80

