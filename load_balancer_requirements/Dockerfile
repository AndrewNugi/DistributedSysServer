# Use a lightweight Python image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file and install Python dependencies
# Ensure that you copy it into the same directory where you'll run pip install
COPY ./load_balancer_requirements/requirements.txt /app/load_balancer_requirements/requirements.txt

# Change directory to where requirements.txt is located before installing
WORKDIR /app/load_balancer_requirements
RUN pip install --no-cache-dir -r requirements.txt

# Copy the load_balancer directory contents into the current directory
COPY ./load_balancer_requirements /app/load_balancer_requirements 

# Copy the myserver directory into /app/server_requirements
COPY ./server_requirements /app/server_requirements

# List files in /app to debug
RUN ls -al /app

# Change the working directory back to /app for CMD execution context
WORKDIR /app

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Command to run the application
CMD ["python", "load_balancer_requirements/load_balancer.py"]
