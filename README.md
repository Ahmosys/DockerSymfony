# DockerSymfony

🐋 This repository is made to contain all the Docker configuration files in order to have an dev environment under Symfony 6.x ready to be used.


## Installation

First, clone the repository into your project folder:

```bash
  $ git clone https://github.com/Ahmosys/DockerSymfony.git
```
Next, put your Symfony application folder into ```DockerSymfony``` folder.

Once this is done, since we are using Apache, please change the correct path of your project in the vhosts.conf file in the ```php/vhosts/``` directory:

```bash
  $ cd  DockerSymfony/php/vhosts/
  $ nano vhosts.conf
```
Once in the editor replace all strings named ```project_folder``` by the name of your folder which contains your Symfony application then save and exit the editor.

When this is done, run the command:
```bash
  $ docker compose up 
```
This will create and launch the containers but also build if it is the first time you run the command the image for PHP 8, Apache, NPM and Symfony CLI present in the Dockerfile in the ```php/``` directory.

And now we're ready! Go to ```localhost:8741``` to see the visual of your Symfony application, for phpMyAdmin go to ```localhost:8080``` and for maildev go to ```localhost:8081```.

*Note : If you want to access NPM, Symfony CLI or Composer you must enter the container where these services are located:*
```bash
  $ docker exec -it www_docker_symfony bash
```
When you are in the container enter the command:
```bash
  $ cd your_project_folder/
```
And that's it! You can use the ```composer```, ```npm```, and ```symfony``` commands :)

## Feedback

If you have any ideas for improvement don't hesitate to open a pull request! It's always a pleasure :)


## Authors

- [@Ahmosys](https://www.github.com/Ahmosys)


## License

You are free to use the code in this repository under the terms of the [0BSD](https://github.com/Ahmosys/DockerSymfony/blob/main/LICENSE).

