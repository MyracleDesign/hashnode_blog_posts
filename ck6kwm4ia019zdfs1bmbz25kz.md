## Setup a Flutter Web Project on GitHub Pages

After my last [blog entry](https://dev.to/myracledesign/my-flutter-journey-3ndj), I got asked how I created a web project in Flutter and how I managed to deploy it. So join me on the journey how to create a Flutter web app and implement the whole thing on GitHub Pages.


%[https://youtu.be/54SM24tLlhc]

## Flutter Channels

To enable flutter web, you have to set up your Flutter CLI properly, and after that, you have to make sure you are on the right channel. Today when I write this post, Flutter web is still in beta, so we have to select a branch that supports beta features.

```shell
>> flutter channel
Flutter channels:
*  master   
   dev
*  beta   
   stable
```

The master channel is the current tip of development. It contains the newest changes in the framework, but it is also vulnerable to breaking changes. So that means in the worst case, something is going wrong. The beta channel is a code selection of the flutter team once a month to a branch that contains the newest released features. It is selected and more stable. So if you want to try around, this would be the channel to go.

For more information about the channels in Flutter, take a look [here](https://github.com/flutter/flutter/wiki/Flutter-build-release-channels).

```shell
>> flutter channel beta
# To download the Flutter SDK execute flutter doctor

>> flutter doctor
```

## Enable Flutter Web

After we set the correct channel and downloaded the new version of flutter, we have to enable the web development model.

```shell
>> flutter config --enable-web
Setting 
   "enable-web" value to "true".

>> flutter config Settings:  enable-web: true
```

Now we are ready to go. Next, we have to create a basic Flutter project.

```shell
>> flutter create ./project-name
```

Flutter create will create all the relevant folders for us. If we open up that project, we should see now the folder "web" inside of the project. 

![Folder Structure](https://dev-to-uploads.s3.amazonaws.com/i/3ac9a3cqtopoiiu49wlk.png)

The last step is to run the app. So go into the project folder and run flutter devices. We should see now chrome and Web Server as a choice.

```shell
>> cd ./project-name
>> flutter devices
Chrome     • chrome     • web-javascript • Google Chrome 80.0.3987.87
Web Server • web-server • web-javascript • Flutter Tools

>> flutter run -d chrome
# Should startup your web dev server.
```
After the flutter run -d chrome command, the chrome browser will start up and reveal the Flutter app.

![Basic Flutter App in Browser](https://dev-to-uploads.s3.amazonaws.com/i/goctx0y0q1rj33zx75p1.png)

Perfect, we did it!

![We did it](https://media.giphy.com/media/wrzf9P70YWLJK/giphy.gif)

## Deploy on GitHub

Before we can deploy, we have to create a new repository in GitHub and to use it as GitHub pages, it needs to have a specific naming convention.

> Template: :: GitHub-UserName ::.github.io
> Example: [md-weber.github.io](https://github.com/md-weber/md-weber.github.io)

Now we can create anything that we want in our Flutter app. If we are ready to go, we have to build the app.

```shell
>> flutter build web --releaseCompiling 
lib/main.dart for the Web...                              1.6s
```

After that, your project will contain a build/web folder. This folder contains all the files that you will need to upload to your GitHub Repository. Open a terminal and switch to the folder and push it into your repository.

If you are new to GitHub and Git, this [Guide](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners) could help you.

```shell
>> cd ./build/web

# The following are the steps that I took. They could vary from project to project. 
>> git init
>> git remote add origin 
>> git add .
>> git commit -m "Init Flutter web project"
>> git push
```

After the push, GitHub will take care of the rest. It immediately creates for you an environment and pushes your changes to the website. 

Inside of your GitHub repository, you will find a new Tab called environments. In this tab, you can see how far your deployment process is. 

![GitHub environment](https://dev-to-uploads.s3.amazonaws.com/i/l1qvuyuvqdksqeeeukvw.png)

Now you can navigate to  https://::username::.github.io or my example https://md-weber.github.io/ to see your webpage.

If you get at that stage a 404 error, please try to add the /index.html to your path and now you should see your very first Flutter Web App.

Thank you for reading!