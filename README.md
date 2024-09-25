# gitfolio-on-akash

Gitfolio will help you get started with a portfolio website where you could showcase your work + a blog that will help you spread your ideas into real world.

Check out this [live demo](https://eg2o93ls79fpl3o30e3sl1ovnc.ingress.akash-palmito.org/) to see gitfolio in action on Akash Network.

## Dockerfile
Build your own gitfolio image before deploying it on Akash.

Create Dockerfile file
```
FROM node:alpine
WORKDIR /usr/app
RUN npm install gitfolio -g
RUN gitfolio build <username> --theme dark --background https://images.unsplash.com/photo-1557277770-baf0ca74f908?w=1634
CMD ["gitfolio" "run" "-p", "80"]
```

`<username>` is your username on github. This will build your website using your GitHub username.

Read more about flags on [imfunniee/gitfolio](https://github.com/imfunniee/gitfolio) repository.

## Build docker image and upload to Docker Hub
```
docker build -t <username>/gitfolio:0.1 .
docker push <username>/gitfolio:0.1
```
Don't forget to login using `docker login`.

## Deploy on Akash
1. Create and fund with AKT your [Keplr wallet](https://www.keplr.app/get)
2. Go to [Akash Console](https://console.akash.network/)
3. Use [deploy.yaml file](deploy.yaml) as template for deployment
4. Replace `nemesischill/gitfolio:0.1` with your `username/image` from Docker Hub
6. Open URI from leases tab after the deployment process
