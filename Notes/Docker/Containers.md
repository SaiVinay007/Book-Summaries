
# Get Started, Part 2: Containers

---

* At the bottom of the hierarchy of building an app is a container. Above this level is a service, which defines how containers behave in production. Finally, at the top level is the stack, defining the interactions of all the services.
* With Docker, we can have a portable Python runtime as an imageThen, your build can include the base Python image right alongside app code, ensuring that app, its dependencies, and the runtime, all travel together.
* These portable images are defined by a file called a Dockerfile.

---

* Dockerfile defines what goes on in the environment inside the container.
* Access to resources like networking interfaces and disk drives is virtualized inside this environment, which is isolated from the rest of your system, so you need to map ports to the outside world, and be specific about what files you want to “copy in” to that environment.
* However, after doing that, you can expect that the build of your app defined in this Dockerfile behaves exactly the same wherever it runs.

---

```Dockerfile

# Use an official Python runtime as a parent image
FROM python:2.7-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]


```

* Where is your built image? It’s in your machine’s local Docker image registry:

```javascript
$ docker image ls

REPOSITORY            TAG                 IMAGE ID
friendlyhello         latest              326387cea398
```

---

* Now run the build command. This creates a Docker image, which we’re going to name using the --tag option. Use -t if you want to use the shorter option.

```javascript
$ docker build --tag=friendlyhello .
```

* " --tag=friendlyhello:v0.0.1 " the default tag is set as 'latest' but we can give our own tags by using ':' after container name.

---

* Run the app, mapping your machine’s port 4000 to the container’s published port 80 using -p:

```javascript
$ docker run -p 4000:80 friendlyhello
```

---

Run the app in the background, in detached mode:

```javascript
$ docker run -d -p 4000:80 friendlyhello
```

* We get the long container ID for your app and then are kicked back to your terminal. The container is running in the background.
* We can also see the abbreviated container ID with docker container ls (and both work interchangeably when running commands):

```javascript
$ docker container ls
CONTAINER ID        IMAGE               COMMAND             CREATED
1fa4ab2cf395        friendlyhello       "python app.py"     28 seconds ago

```

Now use docker container stop to end the process, using the CONTAINER ID

```javascript
$ docker container stop 1fa4ab2cf395
```

---

**Publishing image**


* Put the image in the get-started repository and tag it as part2.

```javascript
$ docker login
$ docker tag image username/repository:tag
$ docker tag friendlyhello gordon/get-started:part2
```

* Upload your tagged image to the repository:

```javascript
$ docker push username/repository:tag
```

* Pull and run the image from the remote repository

```javascript
$ docker run -p 4000:80 gordon/get-started:part2
Unable to find image 'gordon/get-started:part2' locally
part2: Pulling from gordon/get-started
10a267c67f42: Already exists
f68a39a6a5e4: Already exists
9beaffc0cf19: Already exists
3c1fe835fb6b: Already exists
4c9f1fa8fcb8: Already exists
ee7d8f576a14: Already exists
fbccdcced46e: Already exists
Digest: sha256:0601c866aab2adcc6498200efd0f754037e909e5fd42069adeff72d1e2439068
Status: Downloaded newer image for gordon/get-started:part2
 * Running on http://0.0.0.0:80/ (Press CTRL+C to quit)
```
