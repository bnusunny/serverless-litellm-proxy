# Use an official Python runtime as a parent image
FROM python:3.8

# Install Lambda Web Adapter
COPY --from=public.ecr.aws/awsguru/aws-lambda-adapter:0.7.1 /lambda-adapter /opt/extensions/lambda-adapter

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Expose the port that your FastAPI application will run on
EXPOSE 8080

# Define the command to run your application
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8080"]

