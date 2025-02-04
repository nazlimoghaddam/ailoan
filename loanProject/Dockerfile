#Base image
FROM python:3.9

# Environment variable for the virtual environment path 
ENV VIRTUAL_ENV=/opt/venv

# Create virtual environment
RUN python3 -m venv $VIRTUAL_ENV

# Adds the virtualenv’s bin/ directory to the PATH
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Set python to run in unbuffered mode 
# (Stops python from buffering outputs)
ENV PYTHONUNBUFFERED 1

# Working directory 
WORKDIR /app

# Add all files into working directory 
ADD . /app

# Copy the requirements file into the working directory
COPY ./requirements.txt /app/requirements.txt

# Install packages listed in the requirements file
RUN pip install -r requirements.txt

# Copy working directory
COPY . /app

# Port to expose
EXPOSE 8000

# Define the command to run your application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]