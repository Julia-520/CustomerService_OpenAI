
# **ML - Create a Customer Support Website with ChatGPT models**
[Google Slides](https://docs.google.com/presentation/d/1ZnbRJZG-zkMsA3IP-2rD7Rj64nMF3ItF/edit#slide=id.p33)

## **Introduction**

This project is to use the popular ChatGPT models to create a customer support website to answer questions from customers about their website.

### OpenAI API Models

#### *text-embedding-ada-002*

OpenAI’s text embeddings measure the relatedness of text strings. Embeddings are commonly used for:

* **Search** (where results are ranked by relevance to a query string)
* **Clustering** (where text strings are grouped by similarity)
* **Recommendations** (where items with related text strings are recommended)
* **Anomaly detection** (where outliers with little relatedness are identified)
* **Diversity measurement** (where similarity distributions are analyzed)
* **Classification** (where text strings are classified by their most similar label)

#### *text-davinci-003*

This model builds on top of previous InstructGPT models, and improves on a number of behaviors that we’ve heard are important to you as developers.

It includes the following improvements:
* It produces higher quality writing. This will help your applications deliver clearer, more engaging, and more compelling content.
* It can handle more complex instructions, meaning you can get even more creative with how you make use of its capabilities now.
* It’s better at longer form content generation, allowing you to take on tasks that would have previously been too difficult to achieve.

<br>

## **Design**

<img width="388" alt="image" src="https://github.com/Julia-520/CustomerService_OpenAI/blob/main/image/image_design(Python).jpg">

1. **Install Packages**

   Set up environment with installing all the packages needed in the requirements.txt file. 

2. **Crawl Data**

   Crawl data from the website and save the data as a .csv file for use later. 

3. **Embedded Text**

   Use the text-embedding-ada-002
   Model to embedded the relevant data from the .csv file. 

4. **Display**

   Run the project with displaying the customer UI and collect questions.

<br>

## **Implementation and Test**

*This project is run on Ubuntu*

![project structure](/Users/julia/Desktop/CS589_AI/homework/CustomerService_ChatGPT_ML/image/project structure.jpg)

<br>

1. **Create Python Virtual Environment and install Packages**

   Install the needed packages if you don’t have it installed.
   ```
   $ sudo apt install python3.10-venv
   ```

   List all needed packages and versions in requirements.txt file.
   ```
   $ python3 -m venv venv
   $ . venv/bin/activate
   $ pip install -r requirements.txt
   ```

   You may need to update your setuptools to make the installation smooth. 
   ```
   $ pip show setuptools
   $ pip3 install –upgrade pip setuptools or 
   $ pip install --upgrade setuptools --user python
   ```
   
   Create a new .env file using the .env.example file then add your API Key there
   ```
   $ cp .env.example .env
   $ vi .env
   ```
   

<br>

2. **Crawl Data**

   ```
   $ python3 crawldata.py
   ```
   

<br>

3. **Embedded Text**
   ```
   $ python3 embedText.py
   ```
   *No payment method linked, not working through since exceed limit of 60 requests per mins.Worked through after adding payment method.*

   Total cost for embedding the data.



<br>

### **Tips on Saving Money for Developing**

OpenAI charges based on tokens, so to minimize the cost of deveopment for this project, I used a small size of data while developing to make the use of the grant given by the platform.

1. Run ```$ python3 crawaldata.py``` to make sure data crawling works

2. Create your own testing data and save it as ```processed/data.csv``` using the same structure as of ```processed/scraped.csv```. 

<img width="388" alt="image" src="https://user-images.githubusercontent.com/54694766/228060450-1c657372-08d7-41cf-b304-af291a6101e4.png">

<img width="188" alt="image" src="https://user-images.githubusercontent.com/54694766/228059942-d5662acf-14f2-4a91-8772-0bc83d7667ac.png">

3. Modify the code in ```embedText.py``` to read csv file ```processed/data.csv``` instead of ```processed/scraped.csv```.

<img width="501" alt="image" src="https://user-images.githubusercontent.com/54694766/228060086-213d5f85-beed-4afc-aabf-605ad3b2d60a.png">

4. Run ```$ python3 embedText.py``` to embed the data.

5. Run ```$ flask run``` to test the project by asking questions about the testing data in browser. 

<img width="481" alt="Screenshot 2023-03-19 211449" src="https://github.com/Julia-520/CustomerService_OpenAI/blob/main/image/Founder.jpg">

6. Once the project is working as desired, link your payment method on OpenAI and embed ```processed/scraped.csv``` then test project with ```$ flask run```.


### *Note:*
I kept crawldate.py and embedText.py seperate from app.py since I only want to crawl and embed the data once to save time and money. 

So, before runing embedText.py, you need to config the OPENAI_API_Key to use the model to embedding. You can also try other models to embedding.

Run in terminal:
```
$ export OPENAI_API_Key=<Your API KEY>
```

<br>

4. **Display**

   ```
   $ flask run
   ```
   
   You should now be able to access the app at [](http://localhost:5000)

   ***Sample Questions and Answers:***

   <img width="366" alt="Screenshot 2023-03-25 222209" src="https://github.com/Julia-520/CustomerService_OpenAI/blob/main/image/Premium%20Price.jpg">
   
   <img width="366" alt="Screenshot 2023-03-25 222020" src="https://github.com/Julia-520/CustomerService_OpenAI/blob/main/image/Founder.jpg">


<br>

## **Conclusion**

**Accuracy**

* As the questions I asked based on my own data and data crawled from the website, the answer is quite accurate.
* I think the accuracy is more determined by the data provided by the website.

**Cost**

* To avoid high charges, we can use less data while developing. 
Use the real data only when the whole project go through as desired. 
* In this project, the embedding text can be run only once to save money.

*Final cost*

<img width="529" alt="Screenshot 2023-03-26 003555" src="https://user-images.githubusercontent.com/54694766/227764890-c2dc08aa-38f7-44e0-8be4-801e77c71ae2.png">

<br>

## **Enhancement**

* Improve UI
* Implementate more APIs for customer services
