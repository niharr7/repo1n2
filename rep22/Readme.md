# The product -- "Email Analyzer" by SGN CodeChefs

Ever found yourself in the situation of a flooded inbox full of emails?

You immersed yourself in this "First Task of The Day", spent the whole morning replying and addressing each and every email

Forgot to reply to important emails before deadline?

Searching for similar queries from customers to evaluate/refer earlier responses?

Want to refer prior production issues to troubleshoot issues at hand?

## What is it?

The "Email Analyzer”, You can now get your incoming email analyzed and classified the way you want it. Depending on your function, there are many ways you can put categories to sort them!

Natural Language Processing: Text Classification – This will help you search similar client queries and earlier troubleshooting for production issues

Predictive Analysis with Deep Learning - Analyze incoming emails on the fly to determine whether you are expected to take an action and automatic alert generation.

Hook the Outlook Add-In to your local instance of Outlook.

Processing by solving a text classification task using multiple classification algorithms.

## Architecture
	A DotNet hook to attach to MS OutLook to capture the incoming emails and pass it on to the Prediction Engine
	Python based Predition Engine to evaluate the incoming data against its model and suggest the Add-In to create an Alert
	
## Tools and Technologies
	IDEs - Spyder, VisualStudio 2019, Jupyter NoteBooks
	Languages - Python 3.7, C#
	Tools - Anaconda, TensorFlow, Keras, SciKitLearn, NLTK, VSTO AddIns
	

## Email Analyzer Features

Smart Prediction model to help in email Prioritization. 

 -  Setting Priorities. For example, you may want to respond to EOD, Revert etc.
 -  Reminders
 -  Clusters
 
## Coding Style

########################Tester Script###################################################

	class CustomModelPrediction(object):
    
		def __init__(self, model, processor):
			self._model = model
			self._processor = processor
			
		def predict(self, instances, **kwargs):
			preprocessed_data = self._processor.transform_text(instances)
			predictions = self._model.predict(preprocessed_data)
			return predictions.tolist()
		
		@classmethod
		def from_path(cls, model_dir):
			import tensorflow.keras as keras
			model = keras.models.load_model(os.path.join(model_dir, 'EmailBotTrainedModel.h5'))
			with open(os.path.join(model_dir, 'processor.pkl'), 'rb') as f:
				processor = pick.load(f)
				
			return cls(model, processor)
    
	test_emails = [
		"please collect the attached information for your groups to have available for the next steps and share with me asap till 06:00 PM today",    
		"Due to an issue in Veracode` you will not be able to access any of the sandboxes in the application profiles. Veracode team is working on this issue. We will update you once the issue is resolved",
		"FYI Rohan, Weekly Off.",
		"Nominate people from your team who would be work with the enabler groups by replying to this email by 13th March 2020",    
		"As you have seen sandboxes have expiration date now. We have documented the sandbox expiration feature and FAQ in the below link.",    
		"We received 2 accounts in April with negative balances that caused us to error out from loading the account. Can you please look into these 2 accounts to figure out why they have negative balances",
	]


	classifier = CustomModelPrediction.from_path(r'.')
	results = classifier.predict(test_emails)
	print(results)

	for i in range(len(results)):
		print('Should I Reply? ')
		for idx, val in enumerate(results[i]):
			if val > 0.6:
				print(ind_encoder.classes_[idx])
		print('\n')



## Why it's cool
	It is making the predictions and creates alerts automatically through the usage of Predictive model and deep learning to help users.

	Useful for support teams to refer earlier email replies can help improve customer satisfaction and improve time to Market.

	Prediction Accuracy is approximately at 95%.

	Clusters for datasets are well formed and have a very good separations.

## WoW factor
	Implementation of NLP and Deep Learning for the Analyzer solutions.

	Usage of Google's TensorFlow and tf.Keras framework for optimizations of the model execution and quicker analysis.

	Two different models for two different sort of issues - Bag of Words and tf-idf.

	On the fly analysis of incoming emails.

	Automatic suggestions based on earlier experiences.

## The Chefs
	Nihar Ranjan Behera - Master Chef
	Sagar Kambli
	Vaishali Khedekar
	Dnyaneshwar Kulkarni
	Rohan Patel