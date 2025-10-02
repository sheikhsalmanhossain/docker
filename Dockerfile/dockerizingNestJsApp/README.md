Creating and dockerizing nestJs project:

### Step 1: Install NestJS CLI

``` npm install -g @nestjs/cli ```

### Step 2: Create a New Project

``` nest new my-nest-app ```

### Go into the project folder:
``` cd my-nest-app ```

### Run the app:
``` npm run start:dev ```
### Browse:
``` localhost:3000 ```
Now we can browse our app locally. lets create a dockerfile for this.

### Dockerfile :
```
FROM node:22.2-alpine
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
EXPOSE 3000
CMD [ "node", "dist/main.js" ]
```
### Create image :
``` docker build -t nest-app . ```
#### Run container :
``` docker run -p 5000:3000 nest-app ```

Now browse localhost:5000 and we can see our app is running.
