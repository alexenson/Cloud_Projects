# Cloud_Projects
Various Cloud Projects




1)	AWS Project - Build a Game with a Continuous Deployment Pipeline from GitHub to S3 | AWS Tutorial
Host the code in GitHub – create a pipeline that will pull that code every time we make a change.
And deploy it out to an S3 bucket.


2)	AWS Project - Build a Full End-to-End Web Application with 7 Services | Step-by-Step Tutorial

 
 

•	A way to store, update and pull the code. Get it into a source control system. 
•	We need to handle permissions for the code.
Using AWS CodeCommit, which is AWS’ source control system. Kind of like GitHub
You could use GitHub for this project but we will be using CodeCommit.
This is where we a going to store HTML files, CSS files and JavaScript files for the site.

AWS has put the code in a public accessible S3 bucket (the HTML, CSS and JavaScript files)
Take the code and create a CodeCommit repo and basically copy our code into the repository, where we can then work with it.
- Create an empty repository in CodeCommit
- Add a policy to your IAM user so you can access CodeCommit. 
- Create Git credentials for your IAM user to allow HTTPS connections to CodeCommit
CodeCommit is a source control repository that uses the Git technology. So we have an additional set of credential we need to get all of this working.
You can have two sets of credentials – but these will let us make HTTPS calls to CodeCommit. 
- Clone the repository (create an empty folder for future code)
AWS CloudShell is a command line interface that runs in the browser
- Copy the project code from the S3 bucket and commit it to the new repo.
Grab the code from the S3 bucket – copy it to the empty folder that we have in CloudShell and commit it to our repo. 

•	we need a place to host the website and also be able to make updates there. That gets deployed automatically
- The service we are going to use is Amplify – you can build and host websites with Amplify.
Good service for particular front end developers.

•	We need a way for users to register and log into the site
- We will use the service Cognito – this used for authentication. With this service you can do authentication by having people register with their own accounts. Or you can use external identity systems like FaceBook, Twitter or Amazon - or other SAML or open ID providers.

•	A way to do ride sharing functionality
- With this functionality a user will request a ride. Then we need to send a Unicorn to their location. 
We are going to use a Lambda function. Lambda is a bit of code (runs serverlessly) that respond to some trigger. In our case the function will be triggered every time a user requests a Unicorn.
•	Somewhere to store and return the ride results.
Second part of this is a DynamoDB database (key value – no SQL database) generally a lighter options that something like a relational database. Where you have to go set up your schema and relationship and everything ahead of time.
Users are going to request a ride that will invoke the Lambda function. The function will select a Unicorn from the fleet. And then record that request in the DynamoDB table – and respond to the front end with details about the Unicorn that is being dispatched.


•	A way to invoke the ride sharing functionality from the browser
-  Here we will use API Gateway – this is a core service in AWS. Especially for decoupled applications, micro services. Used to build HTTP, REST and WebSocket APIs. The perfect way to invoke a Lambda function. 
Because we are using Cognito user pools – we need to create an authorizer. To authenticate calls – API Gateway uses JWTs (JSON Web Token) that are returned by Cognito. So here we are hooking up the two parts by creating this authorizer. 


3)	Building a Game with a Continuous Deployment Pipeline from GitHub to S3

Host the code in GitHub, create a pipeline using CodePipeline, that will pull that code every time a change is made and deploy it out to an S3 bucket.

You create the CodePipeline that will automate and orchestrate getting the code from GitHub every time a change is made and deploy it out to the S3 bucket.   

 


 
 
 





4)	Architect and Build an End-to-End AWS Web Application 
Using AWS services such as, AWS Amplify, AWS Lambda, Amazon API Gateway, Amazon DynamoDB, AWS Identity & Access Management (IAM)

 

•	A way to create/host a webpage.
- You use AWS Amplify - used to build and host websites. 
We will use a text editor to create a simple index.html page. Once the page is created, we will only use Amplify to deploy and host the website. 
This is where users will navigate to in their browsers.

Connector between Amplify and API Gateway – we need a way to get to it from the index.html page 
Update the html code with the API Gateway URL and then deploy the code to Amplify.



•	A way to invoke the math functionality. 
- Where we invoke the Lambda function. Users are obviously not going into the AWS console to run it. We need a public endpoint or URL that can be called to trigger that function to run.
For that we will use AWS API Gateway – this is a core service in AWS where you can build your own APIs. This is the perfect way to invoke a Lambda function. 
- Trigger the math function in Lambda with an API call.



•	A way to do some math.
- Here you use a Lambda function – this will respond to some trigger.
Code that runs (serverlessly) upon some trigger.
We will write some Python code, and use the Python math library to do the calculations we need.


•	Somewhere to store/return the math result to the user.
- Incorporate a database – we need to store the math result and return it to the user. 


•	A way to handle permissions.
- We need to handle permissions between the different parts of the application. 
- We will be using DynamoDB (this is a key value no SQL database (lighter weight) – compared to a relational database, where you have to set up your schema and relationships, ahead of time)
- We need to give our Lambda function permission to write to the database (set permissions on the execution role for Lambda).
- In Lambda – clicking the execution role, we need to add additional permissions to what the role has already. Permissions related to DynamoDB. 

- Update the Lambda function to write to the database. 

--------------------------------------

So, when you enter your numbers in the base field and in the exponent field and click the calculate button. The script on the updated html page is going to call API Gateway, that then going to trigger the Lambda function. Which does the calculation – that gets written to the database and then we are going to get a message returned to us – in the browser through API Gateway.




































5)	Serverless Email Marketing Application
 
 
•	Amazon Simple Email Service (SES) will be used to send the emails.
•	AWS Lambda for email sending logic and personalising the emails.
•	S3 will be used to store the emails and a list of contacts to send to.
•	Eventbridge will be used to set up a schedule and trigger the Lambda function.
•	IAM used to make sure our services have access to do things in the various other services.

Everything that we do is eligible for the free-tier, except for EventBridge’s scheduler functionality.
So if you are inside the free-tier, most what we will be doing is free. But even outside of that the charges will be minimal. 1 or 2 cents.
EventBridge’s scheduler cost 1 dollar per million scheduled invocations per month. We will only invoke it once or twice so practically 0 cents. So from a cos perspective this will either be free or 1 or 2 cents.








 

We will be using a tool called Eraser.io. This is going to make it really easy to diagram things as we are building. We can also keep track of checklists as we go.

  
- Eraser.io (for diagrams-as-code builder) 


Let’s start a new file for the project.
 

 



 
We will call it Tiny Tales Mail Project.

Then we will make a checklist of what you are going to need.
 
We will paste in a few lines.

Then we will make it a checklist.
 
 



- If you want to be able to send and receive emails, there a couple of things you need.
You need addresses or at least one email address to send to. And you need to be able to validate that. So AWS will send you an email and there is a link in there that you would have to click on. So it has to be a valid email that you have access to. This can be a personal email – like gmail or something like that. So make sure you have that.
- You will need an email address to send from. Also one that you can validate. This needs to be from your own domain – like my website.com . This can’t be a personal one. Make you have that.
- You need some basic knowledge of AWS. 
If you are completely new to AWS, you should still be able to follow along.
- Finally you need a text editor or somewhere to write HTML code.

This is what we are building – some high level requirements.
 













We do have some templates to start from.
 

So let’s start with Diagram as Code.
 

Then Cloud Arhitecture
 


This is going to give us more that we need.
 
But if you want to play with this on your own, it’s a nice starting point with some of the components on the here on the right hand side.

We will get rid of everything, except s3 – so we will clean up the code.
So deleting the code and just leaving the s3 bucket.
 











Click on Both view, so you get both your diagram and checklist. 
 

 


















•	A place to store email templates and list of contacts.
create an S3 bucket on the AWS console. 
Inside the bucket you want to store an email template/HTML template – that will send to people. Also a list of the contacts – the email addresses to send to.
You also want to place a CSV file of the contacts you are going to send to.
Simple CSV file where you just need First name comma Email. The emails that you put in here needs to be ones that you can validate. Meaning that you can receive emails and click on a link AWS sends you – if you want them to go through.
- Upload the contacts.csv file and the email_template.html file to the bucket. 


•	A way to send emails.
We now need a way to send emails. You will use Simple Email Service (SES).
Click on get started and then you need to enter the email address that the emails will come from.
Then you need to add a domain. It cannot be something gmail.com – it has to be your own domain.
i.e. tinytechnicaltutorials.com - If you need to purchase a domain you can use Amazon’s Route 53 or other providers like GoDaddy etc.
- Amazon will then send an email to the email address you entered. You need to open it up and click on the link to verify that you actually own the email address. Once you do, you will be able to send emails from that address. 

You can set up a sandbox environment for this – so there will be limits to how many emails you can send. It is not a production environment – in the real world for this you would have to verify a domain and follow those steps.  You entered a domain earlier. You don’t actually have to verify it, unless you want to move into production. If you do – click create identity. This will give you three CNAME records that you need to copy over to your domain provider – i.e. GoDaddy. Then let the changes propagate, which can take up to 72 hours. And at the top click on ‘Request production access’and describe your use case for sending emails.

- To make sure that it work you can click on ‘Send test email’. You can do a formatted or raw email.
Raw email let you input HTML code. Here you would use the example_email.html file/code.

Because we don’t have a verified domain, we need to validate the individual email addresses that we want to send to. These email addresses are in the contacts.csv file. You need to validate those email addresses if you want to be able to send to them.
- The process is called identities – so under the verify email address - click the view all identities and then create identity. For identity type select email address and enter the email address and create identity. An email will be sent to the email specified and in the email click the link to verify. And you can now send emails to that address.

•	A way to “merge” templates with contacts and send them to the email service. (SES)
By merging – meaning that you fill in the first name that was a place holder in the email template so we get personalised emails. 
//Lambda Function Python Code
For this we will be using Lambda – so it is serverless, we are not going to spin up new servers, new EC2 instances. It will be done with a little bit of code and a Lambda function. 
Lambda needs to grab things from S3 – grab the email template and the contacts and bring them back. 
Lambda will go to S3 to grab the information and once it has done that, it then needs to send the personalised emails off to the Simple Email Service (SES) - to actually send them. 
In the AWS console go to Lambda – click create new function and author from scratch.
You will be using Python 3.12 as the run time. The execution role is what gives Lambda permissions to do things and other services. Create a new role with basic Lambda permissions.
Copy and paste the Lambda function code into the Lambda function on the AWS console. Make sure you update the *# red text with your own information. 
In the code we will be working with S3 and SES. Getting the boto3 client for both of those. Boto is the Python SDK for AWS. 

You want to test the function before triggering it from an external source.  So in the console in the Lambda function you need to set up a new test event. 
//Lambda Function Test Event

You need to set the permission and execution role. The Lambda function needs access or permissions to S3 and SES. 
The function will go to S3 to access it and then it goes to SES. 
In the Lambda function on the console – you need to go to configurations and them permissions in and click the role name. 
You need to create a new policy with permissions in it for the access to S3 and SES and attach to the role. //IAM Policy for SES and S3 permissions
 
Once the policy has been created you need to go back to the execution role and attach it.





•	A way to trigger sending of emails on a schedule.
So you need to trigger the Lambda function. There a lot of ways to trigger the Lambda function – you could trigger the Lambda function when you upload a new email template to the S2 bucket. You can trigger it from the console, from the CLI.
In this case we will be using Eventbridge (used to be called cloud watch events).
With Eventbridge you can set up a schedule to trigger it – say daily or weekly – whenever you want to send your emails. 
Go to Eventbridge in the console and create a new schedule. 

In target details you need to invoke Lambda so select that. 



If you want to enhance the project you could do the below.


 







6)	Building a React App with Amplify, Cognito, and CI/CD with GitHub



•	Set up environment.

- In visual studio code terminal – paste the following command:  npm install -g @aws-amplify/cli
This installs the Amplify CLI

- Next we need to configure Amplify – this basically makes the CLI work with your AWS accounts.
We’ll have to set up a new user, configure access keys.
Use the following commend: amplify configure
This will launch a page to the AWS console – asking you to sign in as an administrator account.
 

On the AWS console you sign in as an account with admin permissions but not the root account.
After you have signed into the AWS console – then press enter on Visual Studio Code. 
 

Then on VS go through a few more questions. It will ask for the region you are in. So therefore confirm on the AWS console the region you are in and on VS use the arrow keys to go to the correct region and then press enter.
 








This will launch the amplify documentation, with instructions on what to do next.
 


The following page.
 

Amplify configure is the command you just ran. 
It is giving you a step by step of what is happening. We have already selected the region. So next what we need to do is navigate to the IAM user creation page in the AWS console.
 
Go to IAM on the AWS console > Users and create a new user.
Choose a name for your user and then next.
No need to add it to any groups – instead you want to attach policies directly. 
There is a policy called AdministratorAccess-Amplify.
 

Select that policy name and press next and then press create user.

Back in VS code – once you have created the user on the console – press enter on VS.

Next in VS you have to enter the access key ID and the secret access key for the user you have just created. 

Go back to the IAM console on AWS – click the user.

Go to the Security credentials tab.
 

Scrolling down to access keys.
 

There are no access keys right now, so you want to create them by clicking create access key.
Then on the next screen select the Command Line Interface (CLI).
 

Scroll down and tick the check box that you understand the above recommendation and want to proceed to create an access key.
 

Then press next and then press create access key.
 

You want to copy the access key shown to the clipboard.
 





Go back to Visual Studio.

Paste in the access code and press enter.
 


Then go back to the IAM console to grab the secret key.
 

Then paste the code in VS
 

Then it will ask whether you want to update/create the AWS profile on your local machine – and we want to do that.

Select the name and this will save this information – like the region, the keys and so on, on your local machine. So you don’t have to do this every time.

Press enter
 









•	Create the React app.

In VS Code type the following command.
npx create-react-app <name of your app>

 


This is a vanilla react app


You will see all the different code and everything that we get here.
 


Then change directory into what you named your app and go down that level.
Type the following
cd <name of your app>
 
 

Next we need to initialise the amplify project within the react app. 

Here it will ask you a series of questions – like what you want to name your amplify app in the cloud?
What language are you using?
What is your local IDE? (An integrated development environment (IDE) is a software application that helps programmers develop software code efficiently. It increases developer productivity by combining capabilities such as software editing, building, testing, and packaging in an easy-to-use application.)
To do this 
In VS type the following command.
amplify init

 
It is recommended to run this from the root. We are already in it.

Then enter the name for the project 

This is the name that is going to show up on the AWS console when we go look up our amplify project.
Different from what we created locally on our file system.
You can go with the suggested by VS Code. It is the text in parentheses.

It will then start with the default configuration, based on what it is detecting.
 It sees that we are in VS Code, it sees we are using JavaScript – specifically react.
The source directory path, so where the code is – it is in the SRC file. 

If you are happy with all of that – then proceed with the configuration.

If you said no, then you can go customise those things.

 
The authentication method – we did save the AWS profile that we set up earlier.
You could enter keys again but let’s go with the profile.

We called it amplify-dev-local.

We will select that
 


It gives you some possible next steps here. You could try to add and API – you could try to do amplify push to deploy everything.
 







Now if you go to the AWS console and into Amplify, you can see the React app (myquizapp) that has been created – which we just did from the command line.
 

It created an environment for us called dev. But this is empty – we don’t have any authentication or databases or APIs. Ii is just an empty container for the application.
 



•	Add authentication with Cognito.

Let’s add something to the app – that is going to be authentication using Cognito. 

In VS Code you can add Cognito on the command line by typing the following command.
amplify add auth


 



This will ask some questions about want you want to do. We are going to go with a default configuration that will give us Cognito.  You can do Federation with a social provider like Facebook, Google etc. You can do a manual configuration – but we will go with default and press enter.
 


We want user to sign in with an email so we will select that.
 

We do not want to do any advanced settings.
 


Now we want to push everything out to AWS. So we type the following on the command line.
amplify push

 

Yes we want to continue.  


Cognitois built around the concept of a user pool. Which is basically a pool of users that are going to register and log into your application. 
   

So if we go out to Cognito on the AWS console – we should see a new user pool created for us. 
 
 

Looks like everything has been created correctly.

We don’t have any users yet.
 


Let’s get the UI (user interface) set up enough so we can actually create an account and log in as a new user. 
















Back in VS Code we will open the app.js file. This is the main file for the react application.
We will replace with the code with the code in GitHub.
 

On GitHub it is the App.js code.
 
import React from 'react';
import './App.css';

// Imports the Amplify library from 'aws-amplify' package. This is used to configure your app to interact with AWS services.
import {Amplify} from 'aws-amplify';

// Imports the Authenticator and withAuthenticator components from '@aws-amplify/ui-react'.
// Authenticator is a React component that provides a ready-to-use sign-in and sign-up UI.
// withAuthenticator is a higher-order component that wraps your app component to enforce authentication.
import { Authenticator, withAuthenticator } from '@aws-amplify/ui-react';

// Imports the default styles for the Amplify UI components. This line ensures that the authenticator looks nice out of the box.
import '@aws-amplify/ui-react/styles.css';

// Imports the awsExports configuration file generated by the Amplify CLI. This file contains the AWS service configurations (like Cognito, AppSync, etc.) specific to your project.
import awsExports from './aws-exports';

// Imports the Quiz component from Quiz.js for use in this file.
import Quiz from './Quiz';

// Configures the Amplify library with the settings from aws-exports.js, which includes all the AWS service configurations for this project.
Amplify.configure(awsExports);

function App() {
  return (
    <div className="App">
      <Authenticator>
        {({ signOut }) => (
          <main>
            <header className='App-header'>
              {/* Quiz Component */}
              <Quiz />
              {/* Sign Out Button */}
              <button 
                onClick={signOut} 
                style={{ 
                  margin: '20px', 
                  fontSize: '0.8rem', 
                  padding: '5px 10px', 
                  marginTop: '20px'
                }}
              >
                Sign Out
              </button>
            </header>
          </main>
        )}
      </Authenticator>
    </div>
  );
}

export default withAuthenticator(App);





Copy all the code and replace it with the code in VS Code.
 



We have the quiz functionality in the code, which we have not implemented yet. So we will comment that out for now.
 
 

So comment those out and save it.

Before we run it, there is another thing we need to do – we need to install the amplify libraries that give us the login user interface.







So in VS Code type the following command.

npm install aws-amplify @aws-amplify/ui-react

 



 

We can now run the application, go create an account and log in.

So type the following command. 
npm start

 


That launches on local host, port 3000 in this case (will vary for different user). 
With the following UI, which we can use to create an account or sign in.
 






We will create an account.
 
You need to use a valid email for this, because it will send you code, you have to use to activate the email. 

Enter email and password and create the account.
 


This will email you a confirmation code and you need to enter the code and confirm.
 







The following screen will show – which is a user account.
Because we commented out all the quiz functionality earlier, all we have is a sign out button.
 


Now if we go back and look at our user pool on Cognito in the AWS console.
 

Refresh the users.  
You’ll see that we have one user.




The code that is making this functionality is:
 
Here we are starting with importing the amplify library from the AWS Amplify package.
This is how we are going to interact with different AWS services.

The line makes the authentication work, is the following.
 
Importing authenticator and withAuthenticator – this is coming from the UI react library that we installed on the terminal earlier.

This is how we get the sign in screen and sign up screen functionality.


We also want to make sure that things look good so we are importing the styles.css
 

Then we have two lines for the AWS exports. This hold configuration for various things.
 
You can see the file here.
 
Things like my Cognito region, my user pool ID and so on.

Without much code you are able to get a smooth authentication experience using Cognito.



•	Add functionality and styling to the quiz.
Let’s add some functionality and styling to the quiz. This part is not so important, we just put in a quiz so that there is something fun in the application. Really the Amplify and Cognito part is the main thing.
However, there is some code in the repo you can grab. 

 


Quiz.js

import React, { useState } from 'react';
import quizData from './quizData';

function Quiz() {
  const [currentQuestion, setCurrentQuestion] = useState(0);
  const [score, setScore] = useState(0);
  const [showScore, setShowScore] = useState(false);
  const [selectedAnswer, setSelectedAnswer] = useState(""); 
  const [isCorrect, setIsCorrect] = useState(null);

  const handleAnswerOptionClick = (option) => {
    const correctAnswer = quizData[currentQuestion].answer;
    setSelectedAnswer(option);
    if (option === correctAnswer) {
      setScore(score + 1);
      setIsCorrect(true);
    } else {
      setIsCorrect(false);
    }

    // Delay moving to the next question to allow the user to see feedback
    setTimeout(() => {
      const nextQuestion = currentQuestion + 1;
      if (nextQuestion < quizData.length) {
        setCurrentQuestion(nextQuestion);
        setIsCorrect(null); // Reset for the next question
        setSelectedAnswer(""); // Reset selected answer
      } else {
        setShowScore(true);
      }
    }, 1000); // Adjust time as needed
  };

  return (
    <div className='quiz'>
      {showScore ? (
        <div className='score-section'>
          You scored {score} out of {quizData.length}
        </div>
      ) : (
        <>
          <div className='question-section'>
            <div className='question-count'>
              <span>Question {currentQuestion + 1}</span>/{quizData.length}
            </div>
            <div className='question-text'>{quizData[currentQuestion].question}</div>
          </div>
          <div className='answer-section'>
            {quizData[currentQuestion].options.map((option) => (
              <button 
                onClick={() => handleAnswerOptionClick(option)} 
                key={option}
                style={{ backgroundColor: selectedAnswer === option ? (isCorrect ? 'lightgreen' : 'pink') : '' }}
              >
                {option}
              </button>
            ))}
          </div>
          {selectedAnswer && (
            <div style={{ marginTop: '10px' }}>
              {isCorrect ? 'Correct! 🎉' : 'Sorry, that’s not right. 😢'}
            </div>
          )}
        </>
      )}
    </div>
  );
}

export default Quiz;







Copy all of the code and back in VS Code you want to add a new file under the src folder.
New file – call it Quiz.js and paste all of the code in and save.
Then you want a second file in the same location – src.
This one is called quizData.js .

For this get the code from GitHub.

 
const quizData = [
    {
      question: "What was the first video game ever made?",
      options: ["Pong", "Spacewar!", "Tetris", "Computer Space"],
      answer: "Spacewar!"
    },
    {
      question: "Which company developed the first commercial antivirus software?",
      options: ["Symantec", "McAfee", "Norton", "Kaspersky Lab"],
      answer: "McAfee"
    },
    {
      question: "Which animal is featured in the official PHP logo?",
      options: ["Elephant", "Hippo", "Giraffe", "Lion"],
      answer: "Elephant"
    },
    {
      question: "What does 'HTTP' stand for?",
      options: ["HyperText Transfer Protocol", "Hyperlink Transfer Technology Protocol", "Hyperlink Text Transfer Protocol", "HyperText Technology Protocol"],
      answer: "HyperText Transfer Protocol"
    },
    {
      question: "Which programming language is known as the backbone of the World Wide Web?",
      options: ["Java", "C#", "Python", "HTML"],
      answer: "HTML"
    },
    {
      question: "What is the name of the world's first computer programmer?",
      options: ["Charles Babbage", "Ada Lovelace", "Alan Turing", "Grace Hopper"],
      answer: "Ada Lovelace"
    },
    {
      question: "In what year was the iPhone first introduced?",
      options: ["2005", "2007", "2009", "2011"],
      answer: "2007"
    },
    {
      question: "What was Google's original name?",
      options: ["BackRub", "Googol", "SearchMaster", "WebSearch"],
      answer: "BackRub"
    },
    {
      question: "Which of these companies was not founded in a garage?",
      options: ["Amazon", "Google", "Apple", "Microsoft"],
      answer: "Amazon"
    },
    {
      question: "What does 'GPU' stand for?",
      options: ["Graphical Processing Unit", "Graphics Performance Unit", "Graphics Processing Unit", "Graphical Performance Unit"],
      answer: "Graphics Processing Unit"
    },  
    {
      question: "What is the capital of France?",
      options: ["New York", "London", "Paris", "Dublin"],
      answer: "Paris"
    },
    {
      question: "Who painted the Mona Lisa?",
      options: ["Vincent Van Gogh", "Leonardo da Vinci", "Pablo Picasso", "Claude Monet"],
      answer: "Leonardo da Vinci"
    },
    {
      question: "What is the largest planet in our solar system?",
      options: ["Earth", "Jupiter", "Saturn", "Mars"],
      answer: "Jupiter"
    }
  ];
  
  export default quizData;

Copy and paste it into the quizData.js file you created on VS Code.
These are the questions and answers. 

In the real world you probably want a database or get them from an API etc. 


Back in App.js we commented out line 19.
 

So, un-comment the line so we can import the quiz components.
 


Also, the line 32.
 

 


Here we are placing it on our page. Save the file.
When you save it your page should re-fresh and we have questions.

 



You can see the answers in the quizData.js file if you want to see which ones are correct.



If this is all you want to do, is just run your front end locally on local host and use Cognito on the back end – then you are good to go.

However, in the real world though, it is more likely that you are going to have code in GitHub or another source control repository.  You are going to hook that up to Amplify and host the front end there. 




•	Push local code to GitHub.

We get our code in VS Code currently and want we want to do is push that out to a new GitHub repo.
 

Then we want to set up Amplify to pull from that repo, and Amplify will host the front end.
Also when we make a change to the code in GitHub we want to trigger a new build and deploy in Amplify. 
So basically continuous integration/continuous deployment – CI/CD pipeline that we have set up.



So let’s work on getting the code out to a GitHub repository.
On GitHub create a new repository
 

You can name your repo whatever you want.
Here we call it amplify-cognito-quiz2
 


We will make it private as it is just for me. Push my code out and hook up to Amplify.
 



You can add a README.md file but we will skip that.

We got the remote repository created out in GitHub, now we need to hook things up with want we have going on in Visual Studio Code.
 


For most part you can use the following code.
Instead of add README.md you are going to add a git add . in order to add all the files you hve been working on.
 


But you will need the following URL.
 

So copy that and back in VS Code type the following command.
git init




Initialising the repo for the project.
 


Then type git add .
 
Adding everything we have changed or added to this folder.


Then we type git commit –m "Initial commit"
 
When we type git commit we can add any comment we want.

Then we type git branch –M main
We are going to call that our branch name.
 


Then type git remote add origin <repository URL>
Here you put in your repository URL that you just created.
 
So paste it in.




Finally you want to push everything out.
So type the following command.
git push –u origin main
 


Let’s check whether everything made it out there back in GitHub repo.

 

All the code is there we checked in.


    



So we checked in our code from VS Code to GitHub .







•	Host the front end in Amplify via GitHub (for CI/CD)

Now we need to hook up Amplify to go grab that code out of GitHub and set up CI/CD.

To do that we need to go back to AWS console and go to Amplify.

Here we have the back end environment and we have seen that working. We’ve got Cognito and we can log in, register for a new account and so on.
 

The front end is in Hosting environment.
 
Basically where are all your files - they are in GitHub, because we just put them there.

Press Connect branch. 


 


Select the repository
 

The repository is not showing in the list due to permissions.
It should be called amplify-cognito-quiz2
 






So if you do not see the repo in the list press the View GitHub permissions.
 

Once you have selected the view GitHub permissions button – it will take you to GitHub.
 












Select the ‘Select repositories’ 
 

If you had said ‘All repositories’, that gives Amplify permissions on all your repositories. 

But select repositories and select the repository you created.
 

And press save.
 


You should then be able to go back to Amplify and find the repository.
 

My Branch is called main.
 

Press next.
 







For app name, we will leave it as it is.
 


The back-end should be called something else.
 

You can make sure of that in Amplify
Go to the back-end environment
 










Make sure you select myquizapp for the App name. For the Environment select dev.
 

You want to enable full stack CI/CD, so anytime we make a change in the GitHub repo, that will trigger a new build and deployment in Amplify.


Then we need a service role that gives Amplify hosting access to our resources.
 


Click create a new role
 











Then you just walk through and select all the defaults.
 


Click next
 


It has added the following policy
 

If you are creating a new role from scratch for some reason, you want to make sure this policy is added. Otherwise nothing is going to work. It will fail at the build stage. 


Click next and the following screen will show and select the role name.
 

At the bottom click create role.
 


This is the role we want to select.
 


So back in Amplify you probably have to do a re-fresh and select the role.
 

Scroll down and click next
 

Save and deploy
 










You can watch the progress as it is going along.
 
It’s provisioned and it is building things – so it has gone out and grabbed our code in GitHub doing the build and it is going to deploy it.

Shortly we should be able to launch the URL and see our quiz running in the cloud.
 



It has finished and click the URL
  





Once clicked that will take us to the Amplify app
 
We have a real URL as well, we are no longer on local host.

You should be able to sign in with the email address that was created earlier.
It is still using the same user pool and has the account that was created.



Once logged in we have our questions.
 














To show you that CI/CD is working – if you were to come back to code on GitHub.
 


Click the src folder
 

Let’s say I want to update the quizData.js file

 










We could remove one of the questions.
 

Click the edit button
 

Click edit in place
 

Delete any question you wish and commit the change.









Commit to the main Branch.
 


As soon as that happens – Amplify should detect we made a change and will do the provisioning, building and deployment.
 
