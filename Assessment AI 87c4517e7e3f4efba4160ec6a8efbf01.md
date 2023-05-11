# Assessment AI

[Portfolio template for AE1.docx](Assessment%20AI%2087c4517e7e3f4efba4160ec6a8efbf01/Portfolio_template_for_AE1.docx)

- Brief
    
    # Assessment Task
    
    Artificial Intelligence (AI) is incessantly getting more sophisticated and pervasive with every passing day, if not minute. While it is often deemed as a staple for science fiction fans, its applications in day-to-day life are tremendous. You probably utilise AI and its faction, ML (Machine Learning), in more places than you can probably imagine.
    
    You are asked to develop a working prototype applying appropriate AI methods to solve an identified problem. The product you will build is intended to simulate a real-world problem.  You will also be required to consider legal, social, ethical and professional issues as appropriate and relevant to your software product.
    
    You are required to build a working prototype of one of the following:
    
    •  Automatic chatbot tool (Automated responders and online customer support) A chatbot is an intelligent piece of software that is capable of communicating and performing actions similar to a human. Chatbots are used a lot in customer interaction, marketing on social network sites and instantly messaging the client. You need to propose and develop an approach for an automatic chatbot tool.
    
    You will be expected to demonstrate your working prototype (during a live session or recorded video as instructed by your tutor). You will also be required to send your source code. Your report structure could have the following sections although you need to add more subsections; Introduction, Statement of the problem, Aims and Objectives, Proposed Solution, Prototype Development & AI Algorithms, Limitation and Conclusion. Your submission should consist of the following:
    
    1. Your report (Word or PDF) uploaded separately
    2. Your source code and video of prototype (in a zipped folder)
    
    ![Untitled](Assessment%20AI%2087c4517e7e3f4efba4160ec6a8efbf01/Untitled.png)
    

### *Second:*

- video:
    
    
    ~~Compared to many chatbots, this one being trained on a custom (json) file taking into into account within given categories, the multitude of possible inputs matching them with the suitable output.~~ 
    
    ~~Since there are multiple input scenarios, it enables the program to respond correctly to the same topic recognizing a variety of different way of expression, for example farewell can be said in different way including god bye, see you later etc… .~~
    
    About the training file: 
    
    One of the most indispensable element of the chatbot is the  Training file. It enables the user to customize the subject entirety due to the whole structure of the chatbot. 
    
    It has a simple build up.
    
    **Tags** stands for categories   
    
    **Patterns**: provides examples to the neural network per category, The grammar or the capital letters white spaces does not matter since later each word will be tokenised and lemmatised  to help recognition of the inputs. 
    
    **Responses**: The output. Even though this is hardcoded, there  still can be multiple phrases and had it output randomly. 
    
    **About the training.py:**
    
    Importing all the necessary libraries 
    
    loading the file. 
    
                The first loop prepares the examples, iterates over the patterns and tokenises all words within it 
    
    and then that list will be lemmatized, the way it works, is that it goes back to the root of each word, so for example an input can be spinning, spined, spin or spins the program will recognise it put into the most suitable format that matches the scenario. 
    
    After getting the data ready, the words are converted to binary representation, since the neural network only takes numerical values. It uses the “pickle” module to do it. 
    
              Then comes the machine learning part: 
    
    Where the second loop goes over each word and  encode them numerically and set each word indices values to either zero or one, based on their occurrence in that specific pattern.
    
    It gets randomized to avoid the same output all over again. 
    
    Turning it into a one dimensional numpay array which then gets fed to the neural network. 
    
             Building a neural network in this case consists of a sequential model of 4 linear stack layers. 
    
     The first layer  is a dense layer with 128 units or nodes (also called neurons). The **`input_shape`** parameter specifies the shape of the input data that the layer will receive. In this case,  a one-dimensional array with the same number of elements as the first element of **`training_x`**.
    
    The second and fourth layer is a dropout layer with a rate of 0.5, which will randomly drop out 50% of the nodes in the previous layer during training to avoid overfitting.  This forces the model to learn multiple independent representations of the same data, which can improve generalization to new data.
    
    The final layer is a dense layer with the same number of nodes as the output shape of **`training_y`** is the shape of the output data that the model will produce. 
    
    The model is then compiled with the **`compile`** method, which configures the model for training. The **`loss`** parameter  will try to minimize the loss during training. The **`categorical_crossentropy`** loss function is often used for classification tasks with multiple classes. It measures the distance between the predicted probability distribution and the true distribution. So in English 
    
    It aggregates or scales the outcomes in the output layer so that they all add up to one, and we get a percentage of how probable it is to have that output or that result, so to speak.
    
    Then we run the training. 
    
    **chatbot:** 
    
    After importing all the necessary libraries and the already trained data we have 4 methods. 
    
    1. Is responsible for tokenising and lemmatising the sentences essentially cleaning the sentences 
    2. Giving binary values for the words based on their present in the sentence or not.  
    3. From the softmax outptut in [train.py](http://train.py) , this function computes the likelihood of whether that class is being a result, works by a numerical point system and we set it to above 25 percent. If the input is not larger than the threshold  we will not include that class in the result. 
    4.  is a helper function that is used to find the response for the predicted class in the training data and return a random response from the list of responses for that class.
    
    And finally the assembly, when everything comes together in the while loop. The text recognizer will listen to your mic, once it was recorded the input gets processed by the earlier mentioned way and will be spoken out loud. 
    
- train.py
    
    Tokenization is when  a sentence get split into a list of words 
    
- challanges
    - Due to the that the code was ripped out of an smart assistant, some of the functionalities did not work they should have, which might have been handled in the original code by a different file or method. For example when it came to lemmatising the words the duplicates had to be removed. `all_words = sorted(set(all_words))`
    
    - presumably the original code handled it in a different way, the array had inhomogeneous shape after 2 dimensions. It had to be turned to 1 dimension only for the x and y or 0 and 1 values to work. To correct this mistake, ensured that all entries in the train list have the same shape. One method is to pad the elements with zeros as needed to ensure that they are all the same length.
        
        ```
        max_len = max([len(x) for x in train])
        train = [x + [0] * (max_len - len(x)) for x in train]
        ```
        

- Video:
    
    So we have characters in words and classes, and since neural network takes only integers the program  encode these words numerically and set each word indices values to either zero or one, based on their occurrence in that specific pattern.
    
    Building a neural network in this case encompasses a sequential model of 4 linear stack layers. 
    
     The first layer added is a dense layer with 128 units or nodes (also called neurons). The **`input_shape`** parameter specifies the shape of the input data that the layer will receive. In this case,  a one-dimensional array with the same number of elements as the first element of **`training_x`**.
    
    The second and fourth layer is a dropout layer with a rate of 0.5, which will randomly drop out 50% of the nodes in the previous layer during training to avoid overfitting.  This forces the model to learn multiple independent representations of the same data, which can improve generalization to new data.
    
    The final layer is a dense layer with the same number of nodes as the output shape of **`training_y`** is the shape of the output data that the model will produce. 
    
    The model is then compiled with the **`compile`** method, which configures the model for training. The **`loss`** parameter  will try to minimize the loss during training. The **`categorical_crossentropy`** loss function is often used for classification tasks with multiple classes. It measures the distance between the predicted probability distribution and the true distribution. So in English 
    
    It aggregates or scales the outcomes in the output layer so that they all add up to one, and we get a percentage of how probable it is to have that output or that result, so to speak.
    
    **chatbot:** 
    
    After importing all the necessary libraries and the already trained data we have 4 methods. 
    
    1. Is responsible for tokenising and lemmatising the sentences essentially cleaning the sentences 
    2. Giving binary values for the words based on their present in the sentence or not.  
    3. From the softmax outptut in [train.py](http://train.py) , this function computes the likelihood of whether that class is being a result, works by a numerical point system and we set it to above 25 percent. If the input is not larger than the threshold  we will not include that class in the result. 
    4.  is a helper function that is used to find the response for the predicted class in the training data and return a random response from the list of responses for that class.
    5. 
    
    Dropout is a regularization technique that helps prevent the model from overfitting to the training data by randomly dropping out units in the network .
    
- Introduction:
    
    Write an introduction on Artificial Intelligence, consider some of the problems AI can cause to society, consider the legal, social, ethical and professional issues as appropriate and relevant to your software product on your chosen topic (AI ChatBot/Email Categorisation or Sudoku).
    
    ### You should submit 2 files: - Your report as a word or pdf document (uploaded separately) - Your video recording and source code including any data files as a zip file
    
    ### You will be expected to demonstrate your working prototype. This demo should be recorded (maximum 7 minutes long video) to show the artefact and to explain the main part of the code.
    
- design
    
    After you have identified some design of the potential problem from previous studies and from the literature, propose your design.
    
- intro
- prototype development
    
    This is a major part of the work. All tools/software/libraries/development platform used. **Provide screenshots of your work, code snippets, diagrams etc. and you can refer to the codes that will be submitted.** Talk about the AI algorithms that could have been involved in the prototype (even if you did not manage to implement it). You can also talk about different ways of implementing the solution, what worked, what failed etc.
    
    You can also add a paragraph of how to run your codes (to allow the markers to test it once you submit this).
    
- conclusion
    
    idea
    
    ## **Conclusion**
    
    AI is going to be increasingly used in healthcare and hence needs to be morally accountable. Data bias needs to be avoided by using appropriate algorithms based on un-biased real time data. Diverse and inclusive programming groups and frequent audits of the algorithm, including its implementation in a system, need to be carried out. While AI may not be able to completely replace clinical judgment, it can help clinicians make better decisions. If there is a lack of medical competence in a context with limited resources, AI could be utilized to conduct screening and evaluation. In contrast to human decision making, all AI judgments, even the quickest, are systematic since algorithms are involved. As a result, even if activities don't have legal repercussions (because efficient legal frameworks haven't been developed yet), they always lead to accountability, not by the machine, but by the people who built it and the people who utilize it. While there are moral dielemmas in the use of AI, it is likely to meager, co-exist or replace current systems, starting the healthcare age of artificial intelligence, and not using AI is also possibly unscientific and unethical.
    

Submitted file: 

[AE2 Boldizsar Banfia Report.docx](Assessment%20AI%2087c4517e7e3f4efba4160ec6a8efbf01/AE2_Boldizsar_Banfia_Report.docx)

- data.json
    
    ```java
    {"intents": [
            {"tag": "greeting",
             "patterns": ["Hi there", "How are you", "Is anyone there?","Hey","Hola", "Hello", "Good day"],
             "responses": ["Good to see you again, how can i be of help", "Hi there, how can I help?" , "Hello! How are you today?" , "Hi there! It's nice to see you." , "Good [morning/afternoon/evening]! How can I help you today?" , "What's up? Is there something you'd like to chat about?" , "Hey! How's your day going so far?" , "Hi there! How's your day going?" , "Good [morning/afternoon/evening]! What's new?" ,  "Hello! Is there anything specific you'd like to talk about today?" , "Hey! It's great to see you. How can I assist you?"],
             "context": [""]
            },
    
            {"tag": "goodbye",
             "patterns": ["Bye", "See you later", "Goodbye", "Nice chatting to you, bye", "Till next time"],
             "responses": ["See you!", "Have a nice day", "Bye! Come back again soon.","Goodbye for now! I look forward to speaking with you again soon.","Bye! It was nice talking to you. See you soon!", "Farewell! I hope you have a wonderful [day/evening/weekend]." , "See you later! Have a great day."],
             "context": [""]
            },
            {"tag": "options",
             "patterns": ["How you could help me?", "What you can do?", "What help you provide?", "How you can be helpful?", "What support is offered", "What are my options", "What are my choices"],
             "responses": ["I can guide you through booking an appointment", "reschedule appointment,", "delete appointment", "cancel appointment", "I can help you with booking an appointment", "I can help you with rescheduling an appointment", "I can help you with deleting an appointment", "The best option is to be referred to a doctor"],
             "context": [""]
            },
    
            {"tag": "thanks",
             "patterns": ["Thanks", "Thank you", "That's helpful", "Awesome, thanks", "Thanks for helping me", "Thanks for the help", "Thanks for the support", "Thanks for the assistance", "Thanks for the guidance", "Thanks for the advice", "Thanks for the information",  "Thanks for the support", "Thanks for the assistance", "Thanks for the guidance"],
             "responses": ["Happy to help!", "Any time!", "My pleasure", "Glad I could help", "No problem, happy to help!"],
             "context": [""]
            },
    
            {"tag": "sick",
             "patterns": ["i feel sick", "i am sick", "i am not feeling too well", "i am not well", "I am not feeling great"],
             "responses": ["Okay. can you tell me what's wrong? what are your symptoms?"],
             "context": [""]
            },
    
            {"tag": "appointment",
             "patterns": ["can i see a doctor", "when is the nurse available", "what dates are available"],
             "responses": ["These are the available date :    Next day, within 7 days, within next 14 days"],
             "context": [""]
            },
             {"tag": "next",
             "patterns": ["nextday", "tomorrow", "next week", "next month", "next year"],
             "responses": ["Sure we would book you in and send you a confirmation email for tomorrow", "That's great, we'll book you in for tomorrow", "ok, great!!!, see you tomorrow", "Great, we'll book you in for tomorrow", "Sure, we'll book you in for tomorrow" ],
             "context": [""]
            },
            {"tag": "exit",
             "patterns": ["exit"],
             "responses": ["Sure I will see you later, Take Care!" ],
             "context": [""]
            }
    
       ]
    }
    ```
    
- training
    
    ```java
    {"intents": [
            {"tag": "greetings",
             "patterns": ["Hi there", "How are you", "Is anyone there?","Hey","Hola", "Hello", "Good day"],
             "responses": ["Good to see you again, how can i be of help", "Hi there, how can I help?"],
             "context": [""]
            },
            
            {"tag": "goodbye",
             "patterns": ["Bye", "See you later", "Goodbye", "Nice chatting to you, bye", "Till next time"],
             "responses": ["See you!", "Have a nice day", "Bye! Come back again soon."],
             "context": [""]
            },
            {"tag": "options",
             "patterns": ["How you could help me?", "What you can do?", "What help you provide?", "How you can be helpful?", "What support is offered"],
             "responses": ["I can guide you through booking an appointment", "reschedule appointment,", "delete appointment",""],
             "context": [""]
            },
             
            
            {"tag": "thanks",
             "patterns": ["Thanks", "Thank you", "That's helpful", "Awesome, thanks", "Thanks for helping me"],
             "responses": ["Happy to help!", "Any time!", "My pleasure"],
             "context": [""]
            },
    
            {"tag": "sick",
             "patterns": ["i feel sick", "i am sick", "i am not feeling too well", "i am not well"],
             "responses": ["Okay. can you tell me what's wrong? what are your symptoms?"],
             "context": [""]
            },
            
            
            {"tag": "appointment",
             "patterns": ["can i see a doctor", "when is the nurse available", "what dates are availble"],
             "responses": ["These are the available date :    Next day, within 7 days, within next 14 days"],
             "context": [""]
            },
             {"tag": "next",
             "patterns": ["nextday", "tomorrow"],
             "responses": ["Sure we would book you in and send you a confirmation email for tomorrow", "That's great, we'll book you in for tomorrow", "ok, great!!!, see you tomorrow"],
             "context": [""]
            },
            {"tag": "exit",
             "patterns": ["exit"],
             "responses": ["Sure I will see you later, Take Care!" ],
             "context": [""]
            }
    
            
           
       ]
    }
    ```
    

the heavy file 

C:\Users\donbo\Desktop\AI AE2\CHATBOT--main\venv\Lib\site-packages\tensorflow\python