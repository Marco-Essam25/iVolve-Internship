# Use Python image
FROM python:3.9-slim

# Create working directory
WORKDIR /app

# Copy application code
COPY . .

# Install Flask
RUN pip install flask

# Set environment variables
ENV APP_MODE=production
ENV APP_REGION=canada-west

# Expose port 8080
EXPOSE 8080

# Run the app
CMD ["python", "app.py"]
