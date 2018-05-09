# disclamer
It uses code from this github: 
https://github.com/visionect/digitalsignage
Binary is stored in this repo also.

You should have Ansible installed on your system. Version should be 2.0 or grater.

# Setup

Checkout from git repo.

# Short usage

## install

run: <code> vagrant up </code>
Takes round 5-10 minutes to start.

## Running the app

In your browser run localhost:3000 --> default port

# How it works:
Uses Vagrant for environment. Ansible for provision . I used also vagrant docker provision but just to install docker - nice hack :)

in roles there are:
- docker 
    - all that is docker related - uses dm machine
    - under templates there is docker file - original is under files file
- HandyStuff
    - some nice packages that I like to have installed
- Haproxy
    - to expose port to outside world
- kubernetes
    - needed for km machine - installs what needs and import image
    - under templates is yaml for pod
- myapp
    - it was used for testing and is not used anymore - can be if you change to Old_Docker.j2 in docker task
cd ..

# Problems

- First problem

Ansible does not have fail switch and somethimes ssh timeouts (usually km machine) - I will look into it some day 
If that happens the best way is to do <code> vagrant destroy</code> and then again <code> vagrant up </code> 
You can destroy just machine that failed. 

 - Second problem

Once ansible is run kubernetes machine cannot be provisioned again. I made some tags so that you can skip problematic provisions. This can be resolved with ansible checks but there was no time for this - some day as usuall :)
