
00:00:01
hello everyone my name is Abhishek and welcome back to my channel and welcome to day one of terraform Zero to Hero series before I get started for all the new subscribers let me tell you that this is a seven days of terraform Zero to Hero series I call it Zero to Hero because there are no prerequisites and you don't need to have any prayer knowledge of terraform to get started with this and what exactly are you going to learn in this series don't worry that complete information is already available in the GitHub


00:00:38
repository that I am sharing the repository name is terraform Zero to Hero it is uploaded in my organization called I am viramala you can also find that link in the description so if you scroll down you will find a file called readme.md and in this file I have provided information what you are going to learn on day one day two till day 7 everything is available let's say you want to understand even in a better way what you are going to get from this series you can also watch video called Day Zero it is already


00:01:15
published it is available in the playlist called terraform Zero to Hero on my Channel or you can use the link in the description where I've spent some 30 minutes to explain about the course syllabus okay so I think I've explained enough about what this series is and now I hope everyone understands what you are going to get from this series now let's get started with today's episode that is day one as part of day one we will understand what is infrastructure as code we will try to see how and why terraform


00:01:50
fits into the concept of infrastructure as code after that I will explain why terraform is one of the most required skills for a devops and Cloud engineer these days everyone is asking terraform as a required skill so we'll try to understand why that is happening and after that I'll explain you how to install terraform on Mac OS Linux and windows and especially for this section there is a surprise so please wait for it for people who don't have laptops or you know for people who don't have enough resources on their laptops I am


00:02:29
going to provide a solution so that's going to be really cool so please wait for that and after that I am going to show you how to set up terraform for AWS because this series we are going to focus mostly on the AWS infrastructure so I'll show you how to authenticate to AWS using terraform and that is same thing that we are going to use throughout the series so as part of day one it is very much required for me to explain how to set up terraform for AWS then we will move towards learning how to write your first terraform code as


00:03:06
part of that we will see how to launch an ec2 instance that is how to create a virtual machine on AWS platform using terraform and while doing this we will also learn about the terraform life cycle don't worry about that like I told you there are no prerequisites I'll take enough time to explain about each and everything that we are going to learn today finally I'll just provide some Basics about terraform State file but this is very basic information because we have a dedicated video for terraform State file


00:03:39
so let's say that you are a devops engineer and you are given a very simple task to create S3 bucket on the AWS platform so obviously the very simple way of doing it is you can go to AWS console provide your username and password authenticate with AWS and search for S3 service go there provide bunch of details such as what should be the name of your S3 bucket should you enable or disable the public access do you need versioned or unversion you will provide bunch of details and finally you will get a S3 bucket let's


00:04:24
say probably it takes two minutes of time so you might be thinking that okay it's perfect but what if you get similar requests from multiple teams let's say you got similar requests to create S3 Bucket from 100 teams so the number of minutes that you are taking is multiplied by the number of requests so obviously I think everyone knows here to solve this problem what you will do is instead of manually creating resources on AWS through the user interface you will follow a programmatic approach okay what you will do is you will follow


00:05:02
a programmatic approach where you can use either the AWS CLI or through your scripting knowledge you can interact with AWS apis so every service in AWS whether it can be S3 it can be easy too so the AWS team will develop a API Now API if you don't know what is an API you can simply understand that if you have knowledge of python or if you have knowledge of shell or any programming language you can talk to the AWS Services programmatically through the apis that means you can make calls to AWS instead of logging into AWS you


00:05:45
can simply make a call to that particular AWS service through your program okay so this is a very simple definition of API now you can either use CLI or API and write your code one single time let's say you want to write it in Python so you can use boto3 or you can use the AWS CLI anyways you will write some code to create S3 bucket and nav whether it can be hundred thousand all that you will tell the team is okay there is a script here either you run it or if you don't have access I will run it and in fraction of seconds


00:06:25
your S3 bucket is created or in seconds your S3 bucket is created right so this way what you are trying to do is you are reducing your effort but the main problem is that you need to have programming knowledge right so the request here is very simple that you just need to create S3 bucket but what if you are asked to create VPC plus VPC configuration everything related to VPC plus you are asked to create an ec2 instance and this ec2 instance has to be highly available and you need to create an S3 bucket as an end point to


00:07:04
the vpco right so if you want to do all of these things you need to have good programming knowledge so the cloud providers like AWS what they said is okay devops internets some of you might not have good programming knowledge so what we can do is we will do the heavy lifting and we will introduce something called as cloud formation templates and in the cloud formation templates what you need to do is it is just a template where you can write this template either in Json or yaml now most of the people in the


00:07:47
industry they already know Json and yaml because it's a standard templating language to share the outputs or you know to provide input to any tools already we use Json or yaml so CFT that is cloud formation templates will allow you to write your infrastructure watch carefully what I'm telling they will allow you to write your infrastructure as code so you will just write that I need VPC I need S3 I need etc etc some configuration that is required right in terms of a templating language that is in Json or yaml CFT has


00:08:29
a very good documentation you can just go to the CFT documentation and see how to write that in a Json yaml format that AWS understands right so this way you are writing your infrastructure as code this code can be shell scripting this code can be python coding or this code can be any of the templates such as yaml or Json because you are not doing it manually through the UI you have automated that so that automation again I am repeating it can be a simple template that is in Json yaml format right or it can be in any scripting


00:09:16
mechanism because you are writing your infrastructure as a code we call these kind of tools as infrastructure as code okay so these kind of tools are called infrastructure as code now there are so many infrastructure as code tools that are available in market for example we just discussed for AWS cloud formation templates okay for AWS cloud formation template is a infrastructure as code tool let's say you are working with Azure Azure has similar kind of mechanism where you just need to write your infrastructure in the


00:10:00
yaml format or the Json format that Azure resource manager understands okay so Azure people also have created a infrastructure as code tool which is called as Azure resource manager if you just go to your Azure resource manager documentation you will understand how to provide this Json syntax how to provide this yaml syntax that this resource manager understands and whatever you put here let's say you need a VM in Azure or you need a AKs cluster in Azure or you need blob storage in Azure so just put


00:10:36
it in the format that resource manager understands and it will make a request to Azure and it will create you the infrastructure let's say you are on openstack so openstack also has something similar called heat templates so there are multiple tools in the market for each provider the developers of that provider for AWS the AWS team has created cloud formation templates for Azure Azure team has created resource manager for openstack of course there is something called heat templates that openstack team has


00:11:12
developed now the problem is that now you might be thinking Abhishek perfect I understood what is advantage of uh cloud formation templates what is advantage of basically IAC tools they are super useful I understood about it but now why terraform right when you have all of these tools which is automating the infrastructure which is reducing the efforts of devops Engineers now why should I learn terraform the answer here is very very simple so as it devops Engineers or as people who create infrastructure you


00:11:52
might have to deal with a lot of tools so let's say in your organization you are using AWS and one of the project in your organization is using azure you move to a different company where they are using openstack some other company they are using gcp as a devops engineer how many tools would you learn right or for any people any person who is trying to automate infrastructure they cannot learn so many tools right so terraform saw this problem you cannot learn cloud formation template you cannot run resource manager


00:12:27
of course they have very good documentation but still as a devops engineer it gets very difficult for you to learn all of these things and to add that some of these tools might also require some scripting knowledge so what terraform said is okay don't worry we will come up with a Universal approach that means you don't need to learn all of these tools just learn terraform okay and tell terraform what provider you require or where do you want to automate the infrastructure do you want to automate


00:13:07
infrastructure on AWS tell me do you want to automate infrastructure on Azure provide that do you want to automate infrastructure on gcp don't worry I can do that so terraform is very very important because irrespective of the provider that you are using right if you have knowledge on just terraform that is enough you need to learn how to write terraform templating language which is called as hashic or templating language or it is also called hashicorp language and if you just know this one which we are


00:13:48
going to learn in this series in this entire series I'll tell you some shortcuts I'll tell you how to write this HCL language right I am going to provide you some IDE shortcuts what plugins to use and all of these things which will make you to learn terraform in a very simple way and by learning terraform you don't have to worry about all of these tools like cloud formation templates resource manager key templates etc etc now that's the reason why terraform has become a mandatory skill for devops and Cloud engineers


00:14:22
and the other reason is that these days people are heavily moving their infra heavily increasing their infrastructure to match the customer needs or you know to move rapidly towards uh scalable infrastructure or highly available infrastructure now if you want to create highly available infrastructure doing it manually is not possible and learning all of these tools is not possible so again the only option that is left is terraform now you might be thinking but Abhishek are there no competitors to terraform of


00:14:57
course there are competitors you have tools like cross plane you have pulumi so many tools cross plane sorry so many tools are available in the market but terraform is the Pioneer terraform has started this practice of universal approach where one terraform using the concept of API as code internally you don't need to understand how terraform uses this API code AS concept API as code AS concept but irrespective of the cloud provider because it uses this approach called API as code it will directly talk to the


00:15:36
provider apis so whatever you are writing in the HCL language terraform will see what is your requirement if you want to talk to AWS this htl template HCL templates are converted to the AWS apis if you say terraform that no no I want to automate infrastructure on Azure the HCL code that you have written will be converted to the azure apis and terraform will apply these apis and create your infrastructure that's why it is called apis code as well this is kind of an interview question or something


00:16:14
for you to understand in detail but going back there are alternatives but terraform has started this entire thing so it has a very good community right so terraform has a huge Community it is started by hashicor of course there are some recent things that are going on that terraform is no longer open source they have changed their licensing mechanism but for now as a end user you are not impacted your organization can still continue to use terraform if they are using terraform to create infrastructure only the devops as


00:16:50
service tools companies are impacted let's not go into that because I'll anyways cover that entire thing in some other video I have explained that in one of the previous videos but in this series as well I'll try to cover that somewhere for now I think you understood the concept there are alternatives cross plane is a very good emerging alternative but terraform has the largest market as of now the other tools are not as matured as terraform they are not as simple as terraform that's why terraform is still the bigger one in the


00:17:24
market that's why many people are asking terraform during your interviews now let's see how to install terraform so the installation of terraform is pretty straightforward you have a Windows machine or Linux machine or a Mac anything the installation is very very simple I've also created a document here so everything that we are talking in this episode or all the episodes they are available as MD documents like you can use them as your notes for example here I've explained about infrastructure as code


00:18:01
things are available here white terraform whatever I explained this is also available here so you can use them as your quick reference before your interviews or you can practice them read through them once you complete these videos as well so I'm trying to create this repository as best as possible now so just go to this install.md where I have provided how to install for Windows how to install for Linux how to install for mac and apart from that okay we'll I'll show this but apart from this like


00:18:34
I told you there is also a surprise not surprise actually for people who don't have their laptops some of you might be using your office laptops where there is a restriction that you cannot use tool install tools or for some reason you cannot install terraform on your laptop you don't have resources or whatever is the reason I will also talk about that so that it will be beneficial for those people now the installation like I told you is pretty straightforward you can just go to the downloads page if you are


00:19:06
on Mac OS just click on this download page right here you have how to install for Mac how to install for Linux so you can just copy these commands and install on your machine for example if you're on Mac just select whatever it is uh let's say you are on amd64 okay so you can just run these commands and terraform is installed on your machine that's it it's pretty straightforward if you're on Linux depending upon the distribution that you're on if you're on Ubuntu then again just provide these things and


00:19:40
these commands and your terraform installation is done so let me quickly show you so that you will also understand right so all that you need to do is take a terminal now so I have a terminal right and in the terminal what I'll do is I'll just copy whatever distribution that I am on let's say I'm on fed row let's say I'm on Ubuntu okay you can just copy these commands and paste it on your terminal that's it nothing more than that and terraform is installed on my machine because I am using a Mac I already have


00:20:18
used these commands and it is installed if you're on Windows only additional thing that you have to do let's say you have a laptop that is Windows what you need to do click on the Windows button select what kind of uh thing that you have mostly people have amd64 so you can just download click on the download button and what you need to do is you have to make sure that terraform is installed in your path mostly the installers once you click on the next next next button like click on the download and click on next next and


00:20:56
mostly terraform is installed and configured to your path but if it is not then try to add terraform to your path as well and better use git bash or any other terminals do not go with the CMD terminal that is there by default on your Windows machine because you will face a lot of problems right better use git bash or Powershell git bash is the most easiest ones because most of your comments that you are using for Linux will also work on the git bash so install that now let's say you don't have this option


00:21:31
at all you don't have a machine and you just have your office machine or in your laptop that you have you don't have resources the other thing that you can do is just go to this repository you might have forked this repository right click on the four button and you will Fork this repository and you will see an option here called code spaces okay so you can use code spaces right so just click on the plus button and create a code spaces on the main branch and the beauteous thing here is code spaces is free for 60 hours a month not


00:22:10
beyond that that means if you are using Code spaces you will get code spaces 30 days if you use it for 30 days you will get two hours each day you can use it on your own basis but what this code spaces will give you like I just clicked on the code space and of course because I have done the initial configuration once you configure code space it is easy for the next time there are no things that you have to provide initially it will just take some time to create a code space environment but this is just like a virtual machine


00:22:44
it is actually a container that GitHub is providing you so it is free for 60 hours you can use it it comes with two CPUs and 4GB RAM for 60 hours free session and here if you just type for example let me increase the font so by default if you just search for terraform hyphen FM version terraform will not be installed if you search for AWS hyphen hyphen version AWS will not be installed right what you can do is just go to the search button right here provide this Arrow and say add Dev container configuration files


00:23:30
this is very simple step just watch for couple of minutes and your terraform and AWS will be installed in your GitHub code space what is GitHub code space GitHub code space is a Sandbox environment or you can consider it as a container environment that GitHub is providing you free for 60 hours if you are using 2GB RAM and 4 sorry 4C 2 CPUs and 4GB Ram so here just type whatever you require so in my case I am looking for terraform oh sorry so modify your active configuration click on that button and


00:24:10
search for terraform okay so you will find something with this Arrow which means verified so select this option it installs terraform TF lint and TF grunt on your machine on your code space environment click on the OK button keep defaults right now you will see a new file will be added which is called devcontainer.json and here you will see terraform configuration but till now terraform is not installed if you again do terraform hyphen iPhone version terraform is not installed you have to do one additional step but before doing


00:24:55
that step I want to install AWS as well so again provide that right arrow and search for add Dev container configuration file click on modify your active configuration and search for AWS so the first option that you see click on the OK button keep defaults and now what I am going to do this is the final step what you need to do here is just say right arrow rebuild and click on rebuild container so it will ask you do you want me to rebuild now what it is doing is it is trying to rebuild the container the dev


00:25:38
container that GitHub has provided you as part of code spaces right so what will happen with this is you will get a new container environment for you again that is totally free for 60 hours but this time your container will have both terraform and AWS CLI installed for you so this is a very good option for people who cannot install terraform on their machine for any reason you can use ec2 instances you might be thinking that Abhishek I can use ec2 instance as well but the default ec2 instance that is


00:26:15
free of cost it comes with one ram right it comes with one CPU and 1GB RAM and if you try to install Visual Studio code or if you try to set up graphical user interface then that instance will not support So for that reasons and because we are going to do a lot of practical learning in this terraform Zero to Hero you can use this code spaces approach for any theoretical learning you can watch my videos and when it comes to practicals you can use this if you exceed 60 hours of time create a new GitHub repository and in that GitHub


00:26:51
repository again configure your code space so that you get additional 60 hours of time right so it will take some time this entire thing for you to create a new container Dev container environment it might take five minutes it might take 10 minutes but once it is done you will get a Dev container Visual Studio code setup that is already there for you along with that you have AWS and terraform installed I am going to show you so it will take like five to ten minutes so let me pause this video yeah so now the environment is created


00:27:28
so you don't have to delete this file do not delete this file you can keep it in your code spaces environment and now if you search the terminal right so just close all of these things this is the same visual studio environment that you can set up on your laptop and when you practice terraform I'll highly recommend you to have Visual Studio code installed because that way you can practice things through an IDE real time people do in their organizations is that they use some IDs it can be Visual Studio code it


00:28:04
can be IntelliJ and vs code is best suited for these kind of things so let's use it and here now if you search for terraform hyphen hyphen version you will see terraform is installed AWS hyphen hyphen version you will notice that AWS CLI is also installed and because you have created this through the rebuilding of container you can Co you can just close this code space now I have closed the clothes code space and if I go back and just refresh the page right and see here this is the code space that


00:28:44
I have on the current Branch super dummy journey is the name that is given click on that and your code space will relaunch and still you will have both the terraform and AWS installed so that way GitHub has given you a dedicated machine and in that machine you have all the configuration that is required to practice throughout this course so one final time I'll just show you terraform hyphen FM version perfect it is already there AWS hyphen iPhone version it is already there and here you can explore the files right


00:29:21
day one files are here day two files are here and from here you can also execute your terraform scripts right so everything is available but only condition is it is available for 60 hours per month if you want to use more than that either you pay for GitHub code spaces or you create one more GitHub account it is totally up to you and if you have a perfect laptop where you don't have any concerns then install Visual Studio code on your laptop install terraform install AWS CLI I'll be talking about AWS configuration in a


00:29:57
couple of minutes but for now I hope that terraform installation is clear and vs code setup is also clear so vs code setup I'm not deep diving into it because you can just download vs code by following some resources just come here and search for vs code download I hope most of you might already have it if not just go to this reference and download vs code right terraform also just go to this page and download if you don't have resources use this example perfect now I hope I can go to the next topic


00:30:32
I have explained this in the last classes as well so if you have an AWS account if you don't have an AWS account please watch my AWS devops 0 To Hero Series where I have explained how to create an AWS account and if you already have what you need to configure terraform for AWS is just go to your root user of course you can use IM user and in your organization it is recommended to use IM users only because even a devops engineer or Cloud engineer will not have the root access so you will create an IM user but because this


00:31:11
is the first class and I don't want to complicate it what you can do is go to your root user or IM user go to the security credentials Tab and all that you need to do is fetch the information of your AWS access key so this information if you just scroll down you will have something called access keys so let's say let me delete one of the access keys right so click on the actions delete just type this deactivate delete so what you need to do you need to click on create access key say that I understand creating a root


00:32:03
access key so because I'm using the root user for the purpose of demo so click on this and your access key and secret access key right both of them are created now go back to your Visual Studio code or terminal whatever you are using in this case I will continue on the code spaces itself so you need to run this command called AWS configure people who have watched my previous series they are well aware of this concept if you have not watched the previous series and if you don't have AWS account please create AWS account


00:32:40
first and then follow these steps now run AWS configure it will first ask you for AWS access key ID copy this one provide it here steps will not differ any terminal that you are using then copy this one provide it here this is your secret access key no problem I'll delete them right after the video default region so you can just select Us East one default output format you can say Json and that's it your AWS is no configured to verify just run commands like AWS S3 LS to just make sure that you are


00:33:28
authenticated to AWS now I just said AWS S3 LS and you see it has listed all the S3 buckets that means now my GitHub code spaces is able to authenticate to AWS understand it carefully my GitHub code spaces is able to authenticate to AWS still now we did not write any terraform code till now terraform cannot authenticate with AWS this is just step one and in step two we will write terraform provider.tf file or we will write a terraform file and there I will show you how to configure AWS for terraform right I'll just show you in a


00:34:10
minute but before that I hope this step is clear and to verify what you can also do is go to your AWS UI create S3 bucket and run this command so that you can understand if this is perfectly configured or not so let me quickly delete this one here itself because you should never share any of this information right you should not be sharing your access keys or you should not be sharing your IM user details with any of the team members as well because it is very sensitive information so now I have


00:34:49
deleted it right so I'll reconfigure after this video or I'll just stop the recording and reconfigure so that my security details are not compromised perfect now let's go ahead and see how to write this thing for terraform how to configure AWS for terraform that would be our last configuration step so you go to the GitHub repository right here in the day one folder you will find a file called projects so this is a folder basically for every project that we are going to do in this I am going to upload


00:35:33
folders so this is the first project that we are doing and what we are trying to do is we are trying to authenticate to AWS and create an ec2 instance that is our first terraform script that we are going to write and for that purpose I have already uploaded the file the terraform file you can also view that in the code spaces uh view so here you can click on day one folder you can also open it in your Visual Studio code and click on this main.tf button right so this is the terraform configuration that


00:36:05
is going to do the magic for us now you don't have to worry what is a provider you don't have to worry what is resource because we are going to cover that in detail for now I'll just give you a basic information what we do in the main.tf file firstly we explain terraform whenever we are writing code in terraform terraform does not understand are you writing this script for automating AWS are you writing this script for automating Azure or anything so what we need to do is in our Visual Studio code environment or


00:36:40
terminal we need to create a file you don't have to create this inside a folder you can create it anywhere just name the file as main.tf the name can also be changed but the reason I have changed I have named it as main.tf is because this is the main configuration file right it is always a good practice to name a file as main.tf which holds the main configuration of your terraform script so I have called it as main.tf but you can call it as abhishek.tf as well inside the main.tf the first thing that you write here is


00:37:20
what is your provider configuration and this syntax you just have to learn for one single time so this is a comment that I've put you don't have to put this comment this is just to say that you can use any environment you can just say us each to us West one anything right so you just need to learn this configuration one single time this is also beautifully explained in the terraform documentation you can copy it from there as well but from anywhere you just say what is your provider that is where terraform has to automate the


00:37:56
infrastructure followed by that you will say if it is azure just replace this with Azure if it is gcp just replace this with gcp so provider AWS in the brackets you have to mention what is the region and what this step will do this step will verify if terraform has access to the AWS or not when you run a particular command I am going to tell you what that particular command is but right now why do you write this block you are explaining terraform that AWS is the infrastructure where I want to automate and region is Us East one


00:38:36
now after that you have to provide resources that you want to create if you want to create 10 resources you will write 10 such blocks okay if you want to create 15 you will write 15 such blocks on a very basic level I am explaining so I have written this one now in the resource block what I have written is what is the resource that I want to create AWS underscore instance now you might be asking but Abhishek how do you know this very simple you can just go to Google search for terraform AWS right so this is hashicorp documentation


00:39:16
where you can search for this synth access for the very first time nobody will know about this one nobody is expert even when I have learned terraform I copied even for now sometimes I just go to the terraform documentation and copy it from here during the advanced demos you will see I will go to this terraform documentation I'll copy some references from here or sometimes I might be writing as well because I am very used to it but for now what you need to do is go to the terraform documentation you


00:39:52
want to create ec2 instance right in the filter just search for ec2 okay so here you will get options what you want to create within ec2 I want to create a ec2 instance so keep scrolling you will find this particular thing click on that button and terraform will give you some examples of how to create ec2 instances right so what is it saying that these are some syntaxes example usage is create basic example with AMI lookup no I don't want that one right here spot instance example Network and credit specification if you


00:40:36
want to create some Advanced ec2 instance configuration if you want to create CPU options with examples what you want to create or you want to just create a very basic one then this is the syntax so I want to create a very very basic one so I will copy this configuration and that's what I did even here if you see here I have a very basic instance configuration so even if you don't know anything about terraform you can just copy it from the documentation but as you keep writing right as you keep writing this terraform


00:41:11
files you will learn about it the only prerequisite here is you need to have the knowledge of cloud provider if you don't have the knowledge of cloud provider let's say you want to use terraform with AWS you need to have good knowledge on AWS without AWS knowledge it is impossible for you to master terraform right because using terraform what you are doing you are creating step by steps on AWS so that's why I created the AWS 0 to 0 and after that I am doing terraform Zero to Hero right so I just copied this one


00:41:46
I don't need host Resource Group I don't need tenancy so I just removed these things and this is exactly what I have pasted here right so provider is default thing that you write in every terraform script that you are doing after that any resource that you want just go to AWS documentation copy paste it in future I am going to tell you more and more tips and tricks as well but for now as part of day one this is what we are going to do now okay I've provided AWS security credentials using AWS configure command so my


00:42:25
uh terraform using this provider block it will understand that it has to talk to AWS and the credentials are also stored on this machine so terraform can use those credentials after that I have provided that okay this is the code this is easy to instance that I want to automate what after that after this what you have to do so after this what you have to do is you have to run a bunch of terraform commands right so this bunch of terraform commands will help you to create infrastructure right now you just wrote the files but the


00:43:02
first terraform command that you are going to do is called as terraform init now what this terraform init will do it will initialize the configuration this command will do the magic for you this command will read the terraform files and here it will understand that okay I have to fetch the AWS credentials so let me initialize that configuration for you so as part of terraform init when you run this particular command okay what does it say terraform initialized in an empty directory the directory has no terraform configuration


00:43:39
files why because I did not switch to the right directory within this repository I have to go to day one folder right and inside the day one folder what I need to do is I need to go to this folder called project okay all all of you what you need to do is you have to clone this GitHub repository onto your local machines and then you have to run this particular commands now I am inside that folder so I can run terraform init so now see what is it doing initializing provider plugins where did it get this


00:44:21
provided plugins so it read from your terraform file that you want to use provider AWS so it is getting some default plugins and it said that perfect your terraform has been successfully initialized now I can talk to AWS now what I have to do next so you have to tell terraform to apply the configuration so the command for that is terraform applied but before applying there is one very good thing that terraform provides which is called as terraform plan what is plan is just like a dry run it is a dry run


00:44:59
where before creating the infrastructure or before applying the infrastructure you can use this terraform plan command and it will show you what exactly it is going to create understand it carefully it is not creating the infrastructure but it is just telling you when you run the plan command it will show you that Abhishek if you run the terraform apply after this one I am going to create all of these things are you okay with it right so it is just like a dry run or it is just like a verification that you are going to use


00:45:38
within the terraform to automate the infrastructure okay something has failed here let me see what exactly it is okay uh any guesses here why uh this is failing so this is basically failing because I have deleted uh the security credentials right so what I'll do is I'll just pause the recording so couple of minutes back when I was explaining you people I've deleted the credentials so what I'll do is I'll pause the recording I'll create the credentials one more time and I'll show you after that how does this


00:46:15
plan command work right so let me just pause recording okay I have configured it now let me run the terraform plan command I hope it will work enough if not we will try to fix it right so debugging will be part of this series where I am not going to edit any of the things perfect what is it saying now see this is the output of the plan command and whenever you are running the plan command please spend a couple of minutes and try to see what exactly your terraform scripts are doing because sometimes you might do a very simple


00:46:53
mistake and this plan comment can act as a savior before creating it is telling you what exactly are you going to perform right so what I usually do is whenever I run this plan command I take couple of minutes and I read through everything here it is saying that Abhishek terraform will perform the following actions it will create a resource called AWS instance and this will be all of your details right will be known after applying that means right now it does not know what would be the details right


00:47:28
because the network interfaces and all of these things it is not aware but it can give you example uh sorry information such as instance type is going to be T2 micro how did it say that because you have provided in the TF files it can also give you information about Ami because you have provided the Ami details right perfect now that is what it is saying that one resource will be added 0 will be changed and 0 will be destroyed perfect so now what I can do because I am comfortable with it I can go ahead


00:48:03
and run terraform apply now if I apply this configuration you will see a instance is created if all of these details that I have provided is correct it is asking again it is asking like one more step confirmation click on the yes button and terraform will create ec2 instance if the Ami that you have provided is correct if the instance type that you have provided is correct let's say if this Ami does not exist on the cloud provider it will not create that's what AWS has said and I intentionally did it because I want to show you the


00:48:42
error so here AWA said that okay the Ami that you provided does not seems to exist so what I can do is I can go to my AWS right let me go to my AWS here and click on ec2 perfect here I can pick up any Emi Ami sorry not Emi so here you can go to instances if you don't know how to get Amis there are different ways but if you are a beginner click on the launch instance and pick up any Emi that Ami that you want so here uh let's say I want to use this one Ubuntu okay so here you will get the Ami details so you can just copy paste this


00:49:27
one let's say you can select here and uh okay how do I copy this one what is the easy way I can copy it from here okay very bad perfect so let me just take this one and update this one here and if there will be any other issue I am going to fix it right so let me run this command one more time terraform apply and again it will ask you are you sure about the configuration that you want to create click on the yes button there are ways to avoid it you can also ignore that yes as an input but for now let's restrict


00:50:14
it now again you run into an error what does it say creating ec2 instance missing input no subnets found for default VPC please specify a subnet status 400 right so what is it saying so it is saying that you have provided Ami you have provided instance type but what should be is my sub method so this is the reason why I told you that you need to have understanding of the cloud provider let's say you don't have understanding of AWS itself now you will not know what does the subnet mean here what does the VPC mean here how to


00:50:52
create that configuration right so for that purpose I did not complete this configuration to show you that you need more details you need to understand the cloud provider configuration to create resources right so what I'm going to do here is I am going to update these details and I will rerun so what I'll do simply is go to the VPC configuration right so this is my default VPC so just go to your AWS dashboard and click on the subnets button let's say you don't have any subnet you can create a subnet or if you


00:51:28
already have a subnet like in my case this is my default VPC right and here I already have a subneter so I can use this subnet as well copy paste this one go back and here just say subnet underscore ID is equals to this now if you have seen I am getting this Auto completion right so whenever I just type sub you will see some suggestions here now why are you seeing that suggestions is because I am using something called as HCL plugin so just click on your extensions button and here you can install this particular plugin called


00:52:10
hashicorp terraform right if you just search for hashicor you are going to get this one and just search for HCL yeah right so hashicor HCL syntax also install this one perfect so install hashicor and install this hashicorp HCL I am I will tell you what is the advantage of using this hashicorp HCL plugin it will help you with linting it will help you with other things as we progress with this series but for now just install those two plugins so I have provided the supply details as well and along with this you can also


00:52:50
provide key value pair right so let's say in your account you already have a key value pair what you will do is just go to your account search for key pair ec2 and here you will have key pairs if you don't have key pair create a key pair because key pairs are useful to log into the instance so I already have a key pair called AWS login so let me just copy this one and enter now I hope this is complete and I hope it works so let me try this one more time terraform apply see this is part of debugging of course


00:53:38
this is a very simple one and I've done most of the things intentionally because you people are just learning terraform so I thought I will put the wrong Ami I'll put you know the I'll ignore the subnet details so that you will understand what is the error and how to fix it but two things you might have understood by now is one is when you are using terraform you should have knowledge on that particular cloud provider and the second thing is you need to have some plugins and good idea of how to use the terraform


00:54:11
documentation and that way that's where I'm going to help you throughout this series I will make sure that you will Master the terraform documentation how to use a terraform documentation and write the terraform Scripts perfect so if you see here it says apply apply complete let's go to the AWS dashboard click on ec2 and let's see if the ec2 instance is created one instance is running is the name of the instance example so what did it say this is the instance ID perfect let's go and see here of


00:54:49
course the name is not created because I did not give the tag but the instance ID should be this one it should end with 3d7 3d7 perfect so the instance is created and clap for yourself you have created your first terraform script to create AWS ec2 instance and I will submit these things to the GitHub repository or let's give it as an assignment so I already have these things here right if you go to the terraform Zero to Hero the entire project is already uploaded but I have ignored the subnet and I have ignored


00:55:29
the key pair because you will run into some errors and let's see how many of you will be able to fix that way you will run your first terraform script right so till now what did we understand we have understood why terraform what is the importance of it how to write your first terraform we have all the things documented here so take it as a recap for today's video and watch it finally one thing that is left for me to explain is what is the terraform State file so like I told you in this video it is


00:56:04
not that important but if you just do LS you will see that there is this file created called terraform.tf state and if you just do cat on this file you will see that terraform has updated this file with lot of details now what exactly these details are so terraform makes use of this state file right it uses this state file to record whatever it is creating so next time when you write a new terraform script or you will add more script to this like instead of along with this easy to instance let's say here you will write


00:56:42
resource right let's say uh S3 bucket or you want to do you want to create a EBS that is supporting this ec2 instance or whatever it is so how does terraform know that previously you have created ec2 instance so to record that information terraform makes use of this state file in the future classes we will learn about this state file how to secure sensitive information in the state file how to use remote State file local state file how to run terraform in the CI CD all of these things we will learn where we will


00:57:18
focus more on the state file but for now don't get confused why is this file created it is used by terraform to record whatever infrastructure it is creating right and finally once you are done with this demo just run this command called terraform test drive and what terraform will do is terraform will look at the state file and understand okay I have created an ec2 instance Abhishek is asking to destroy so let me destroy that ec2 instance so that you will not be built right so always when you are performing the demos


00:57:52
final thing that you have to do is to run the terraform destroy command and just say yes and you will notice that the ec2 instance that you have created will be destroyed as well so this is a complete life cycle of terraform terraform init terraform plan terraform apply and terraform destroyed what did we learn the life cycle of terraform is four phases init which will initialize the terraform configuration it will get the sensitive information sorry it will get the password it will authenticate with AWS


00:58:26
it will do the provider configuration then terraform plan which will show you what exactly is being created terraform apply which applies the configuration and Destroy which destroyed if you go back refresh you will see the ec2 instance is deleted perfect so this is the terraform demo for you and this is day one and day two three four five six seven are going to be super exciting and I hope you like this code spaces trick as well and that is the reason why I perform today's entire video on the code spaces because I want


00:59:06
you people to be acquainted with it when you move to organizations you might see people using something like this and you should not be scared you should not be thinking okay what exactly these people are using why are they not using their laptop what is code spaces why are they doing everything here so it is something like uh a trick or something or you know something very cool that you can use you don't have to create dependency on your laptop tomorrow you go to your friend's house you go to your colleague's house


00:59:35
you can just log into your GitHub from their laptop and you can access your code spaces so it will remove the dependency of your laptop perfect so use this trick even if you have your laptop just try to do it on code spaces it's super cool thank you so much for watching today's video I hope it is informative take care everyone see you

