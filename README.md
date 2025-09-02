# AWS-Project (AWS-Lambda + SQS + DynamoDB + NodeJS)

Learning project where a POST API in NodeJS receives a transaction payload (idempotencyId, amount, type: credit/debit).

This route executes a function that places the transaction in an AWS SQS (queue), using the AWS SDK.

Along with it, an AWS Lambda function connected to this SQS picks up each message and saves it into an AWS DynamoDB database.

A test script was created to generate 100 different transactions and make the POST request.

A simple page was built using Next.JS that displays the transactions saved in DynamoDB through a GET route.

Link to the front-end: https://github.com/RenatoSouzaAN/Projeto-Aprendizado-AWS-Frontend

## Backend part of the project

Project Backend

This part of the project consists of essential files for the backend.
Main Files

  App.js

      This file contains the main logic of the backend application, using the Express framework to handle HTTP requests and the AWS SDK library to interact with AWS services.

      Features:
            Implements a POST route ("/transaction") to receive transactions and send them to the SQS queue.
            Configures the AWS SQS client to send messages.

      Usage Instructions:
            Make sure to have the dependencies installed by running npm install.
            Start the backend with the command node App.js.

      Troubleshooting:
            If you encounter AWS configuration issues, check that the credentials in App.js are correct.
            Ensure that the SQS service is properly configured in AWS.

testScript.js

    This script performs integration tests, simulating transactions sent to the backend.

        Purpose:
            Generates random transactions and sends them to the backend to test the flow.

        Execution Instructions:
            Before running the script, make sure the backend is running.
            Run the script with the command node testScript.js.

        Test Reports:
            Test results will be displayed in the console.

  index.mjs

    This file is the main entry point for the AWS Lambda function. It receives messages from the SQS queue and saves them in DynamoDB.

        Features:
            Connects to the SQS queue and saves transactions in DynamoDB.
            Uses the AWS SDK library to interact with DynamoDB.

        Configuration:
            Make sure AWS credentials and region settings are correct.

        Deployment Instructions:
            Package the compressed files in the "teste" directory for deployment in AWS Lambda.
            Configure the Lambda function to be triggered by the SQS queue.


Tests

The test script testScript.js sends simulated transactions to the backend and displays the results in the console.

Troubleshooting

    AWS Credentials:
        Verify that the AWS credentials in App.js are correct.

    SQS Configuration:
        Ensure that the SQS queue is properly configured in AWS.

Additional Information

    Project Structure:
        Make sure the project structure is organized as described in the README.
        The "teste" directory contains the compressed files for AWS Lambda deployment.
