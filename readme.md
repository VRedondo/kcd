# Code, Build, Deploy: Nx Monorepo, Docker, and Kubernetes in Action Locally

### Step 1 - Setup your NX workspace

Let's establish an integrated Nx workspace tailored for Typescript projects. The organizational name we'll use is `vredondo`. For the purpose of this exercise, we'll disable Nx Cloud support. Opting for the interactive repository setup, we leverage its pre-configured environment, which conveniently includes all the essential components needed for our setup.

```sh
npx create-nx-workspace@latest --name vredondo --preset ts --interactive --nxCloud skip 
```

After this command runs you will find out it generates essentials resources like package.json with a series of Nx plugins, prettier and typescript are pre-configured as well

Ok with our Nx monorepo in place, now let's start adding our first application, for this exercise we're going to have a Pokemon API build in NodeJS but we're going to be using the power of Nx to speed up our setup process

so let's start by adding the require Nx generator package

```sh
npm i @nx/express
```

With that we can start creating the scaffolding of our API project, the run 

```sh
nx g @nx/express:application --name pokemon-api
```

Ok with that lets explore a bit to see what Nx express generator did for us

Essentially it create a pokemon-api server with express, configure it with typescript, eslint and jest for unit testing purposes, it also create a second project dedicated to perform e2e testing, something important to notice is the project.json file that gets create in each project root, this file is very important for Nx to manage the different task we wanna run on each project like, lint, build, serve, test...and so on and it also helps Nx build the dependecy graph

Ok that's good enough for now, lets now add some content to our new pokemon-api project

....


now that we got our content lets start by adding a nx plugin to start creating our docker image

```sh
npm install -D @nx-tools/nx-container
```

run the task like

```sh
nx g @nx-tools/nx-container:init pokemon-api
```
