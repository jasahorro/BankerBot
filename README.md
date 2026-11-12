<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Build a Chatbot with Amazon Lex

**Project Link:** [View Project](https://nextwork.ai/projects/143bcc99-ef5a-58e7-96f0-45d7c00b761a)

**Author:** Maria Jasmin Ahorro

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to set up and configure an intelligent chatbot named BankerBot using Amazon Lex, define custom user intents and sample utterances, and configure a FallbackIntent with dynamic variations to handle unrecognized inputs.

I'm doing this project to learn how to build cloud-based conversational interfaces, structure chatbot workflows, and manage user interactions and error handling using natural language processing.

### What is Amazon Lex?

Amazon Lex is a fully managed artificial intelligence service with advanced natural language understanding and automated speech recognition capabilities. It enables developers to build conversational interfaces—commonly known as chatbots—into any application using voice and text.

By leveraging the same deep learning technologies powering Alexa, Amazon Lex allows you to design highly engaging, human-like user experiences capable of fulfilling complex requests, handling multi-turn conversations, and dynamically recognizing user intent. It integrates seamlessly with AWS services like Lambda and CloudWatch, making it powerful and scalable for building enterprise-grade conversational bots without managing infrastructure.

### Key tools and concepts

Services I used were Amazon Lex to build and test the BankerBot conversational interface, and Amazon Polly for text-to-speech voice configurations.

Key concepts I learnt include defining custom intents and sample utterances, configuring FallbackIntent with dynamic closing responses and message variations, managing intent classification confidence scores (0.40), and implementing initial responses for natural interactions.

### Personal reflections

One thing I didn't expect in this project was how easily Amazon Lex's machine learning model automatically recognizes variations of user utterances—like understanding "Hiya" or "Help me" even when only "Hi" and "Hello" were explicitly defined—while still reliably triggering the customizable FallbackIntent whenever input confidence dropped below the threshold.

### Project timeline

This project took me approximately 15 minutes. The most challenging part was figuring out how the intent classification confidence score threshold (0.40) behaves when testing edge-case phrases that accidentally trigger the default FallbackIntent. It was most rewarding to customize the FallbackIntent with initial responses and message variations, making BankerBot respond dynamically and sound genuinely conversational and human-like!

### ❤️ Thanks for doing this project!

I chose to do this project today because I wanted to explore cloud-based artificial intelligence and learn how to build practical, conversational interfaces from scratch using Amazon Lex. Something that would make learning with NextWork even better is having more advanced hands-on challenges or automated grading scripts that instantly test our deployed chatbot configurations and edge-case handling.

## Setting up a Lex chatbot

### Approach to chatbot setup

In this step, I will create a new blank chatbot named BankerBot on Amazon Lex, configure its basic IAM permissions, set up its voice and confidence threshold, and choose a preferred bot voice because it establishes the foundational environment and settings required to build and test our interactive banking assistant.

### Chatbot creation process

I created my chatbot from scratch with Amazon Lex. Setting it up took me about 10 minutes to configure the bot details, IAM permissions, voice settings, and confidence threshold.

### IAM role configuration

While creating my chatbot, I also created a role with basic permissions because Amazon Lex needs permission to call other AWS services on your behalf, such as integrating with Lambda in later parts of this project series.

### Intent classification confidence score

In terms of the intent classification confidence score, I kept the default value of 0.40. This means that your chatbot needs to be at least 40% confident that it understands what the user is asking before it attempts to provide a response. If a user's input is ambiguous and falls below this 40% confidence threshold, the chatbot will trigger the FallbackIntent.

![Setting up a Lex chatbot](https://nextwork.ai/overjoyed_magenta_proud_yak/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_97dc2351)

## Intents

In this step, I will create and name a new intent called WelcomeIntent, define sample utterances like "Hi" and "Hello", set up a closing response message, and build and test the bot because it teaches our chatbot how to recognize user greetings and respond appropriately during conversations.

### Creating my first intent

Intents are what the user is trying to achieve in their conversation with the chatbot (such as checking a bank account balance, booking a flight, or greeting a user). In Amazon Lex, you build your chatbot by defining and categorizing these different intents to manage related user requests.

I created my first intent, WelcomeIntent, to greet users when they say hello, recognize common greetings like "Hi" or "Hello," and trigger an appropriate closing response from BankerBot to kick off the conversation.

### Testing chatbot responses

I launched and tested my chatbot, which could respond successfully if I enter greetings I explicitly defined in my sample utterances, such as "Hi", "Hello", "I need help", or "Can you help me?", as well as similar phrases recognized via machine learning like "Help me", "Hiya", or "Good morning".

## Handling unrecognized inputs

My chatbot returned the error message 'Intent FallbackIntent is fulfilled' when I entered phrases like "How are you" or "Good morning". This error message occurred because the confidence score for those inputs fell below the 0.40 threshold, and since no other matching intents were found, Amazon Lex automatically triggered the default FallbackIntent.

![Handling unrecognized inputs](https://nextwork.ai/overjoyed_magenta_proud_yak/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_505be5b8)

## Configuring FallbackIntent

In this step, I will customize the default FallbackIntent message and add custom conversation variations because it replaces confusing default error messages with user-friendly guidance, helping users understand how to interact with BankerBot when their input is not recognized.

### When FallbackIntent triggers

FallbackIntent is a default intent in every chatbot that gets triggered when the chatbot's confidence score for all defined intents falls below the set threshold (such as the default 40%), meaning the user's input is ambiguous or not recognized by any other custom intent.

I wanted to configure FallbackIntent because the default error messages were confusing and didn't clearly communicate to the user that their request wasn't understood. Customizing it allows me to provide helpful guidance and dynamic variations that point users toward what BankerBot can actually do (such as checking account balances, transferring funds, and making payments).

### My FallbackIntent configuration

To configure FallbackIntent, I navigated to the FallbackIntent in my left-hand navigation panel, updated the closing response message to provide clear guidance, and added custom conversation variations to make BankerBot sound more natural and helpful when handling unrecognized inputs.

I also added variations! What this means for an end user is that whenever the chatbot triggers the FallbackIntent, it will randomly select from your defined message variations instead of repeating the exact same sentence every time. This creates a dynamic range of responses and makes conversations feel much more natural, conversational, and human-like.

## FallbackIntent with Variations

![FallbackIntent with Variations](https://nextwork.ai/overjoyed_magenta_proud_yak/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_c4fc89af)

## Initial Responses

In this project extension I'm about to add initial responses and message variations to the FallbackIntent in Amazon Lex I'm doing this so that the chatbot can greet users or acknowledge inputs right at the start of an intent's flow, making BankerBot sound even more conversational, natural, and human-like when it handles unrecognized messages.

### Setting up initial responses

Initial responses are greetings or acknowledgments your chatbot sends right at the start of an intent's flow before anything else happens in that conversation. I've set up initial responses for the FallbackIntent so that when BankerBot encounters an unrecognized message or inputs it doesn't understand, it responds right away with conversational phrases like "Hmmm this is interesting...", "One moment...", or "Hang on.." to make the interaction feel much more natural and human-like.

### Initial response implementation

The initial response messages I set up are conversational phrases like "Hmmm this is interesting...", "One moment...", and "Hang on..." which are sent right at the start of the FallbackIntent's flow when the chatbot encounters an unrecognized message. For the user, this means they get an immediate, natural-sounding acknowledgment before the chatbot provides further guidance, making the conversation feel much more conversational, human-like, and engaging.

![Initial Responses](https://nextwork.ai/overjoyed_magenta_proud_yak/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_09bcb9701)
