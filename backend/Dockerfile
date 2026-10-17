FROM python:3.13-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements first to take advantage of Docker layer caching
COPY requirements.txt .

# Install dependencies from the requirements file without using cache to reduce image size
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the backend files into the container
COPY . .

# Expose the port your application will run on
EXPOSE 7860

# Start the application using Gunicorn
# - `-w 4`: Uses 4 worker processes for handling requests
# - `-b 0.0.0.0:7860`: Binds the server to port 7860 on all network interfaces
# - `app:superkart_api`: Runs the Flask app (assuming `app.py` contains the Flask instance named `superkart_api`)
CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:7860", "app:superkart_api"]
