# CRM Deduper

Deduplicating address data in CRM systems is important. Duplicate customer data can lead to a myriad of problems that directly impact the quality of customer service, the effectiveness of marketing campaigns, and the accuracy of sales forecasts. Ensuring each customer has a unique record enhances personalized service and operational efficiency, directly impacting business growth and customer satisfaction. 

Our open-source CRM Super Deduper effort is on a mission to streamline the identification of duplicate CRM records for large datasets with a freely available tool.  Leveraging advanced data science methodologies such as TF/IDF scoring, nearest neighbor algorithms, and multi-pass masking, our goal is to transform a complex challenge into a manageable task that completes in minutes on a standard Google Colab instance. 

## Progress 
As of 2/5/2024, we have achieved a 98% recall of duplicates from 174,090 records (15,153,577,005 comparisons) in 11 minutes and 47 seconds. Another test with 75,232 records (2,829,889,296 comparisons) took just 2 minutes and 32 seconds. Deduplicating up to 100,000 records can now be done in less than 10 minutes. We're testing with Google Colab, so anyone can easily use this powerful tool with readily available resources to achieve similar results.

## Instructions
The deduplication process is streamlined for simplicity and efficiency:

* **Start Easily**: Open an example notebook in a secure, temporary Google Colab session.
* **Load Your Data**: Import a CSV file of addresses exported from your CRM.
* **Customize Configuration**: Tailor the settings to meet your specific requirements.
* **Execute the Process**: Run the deduplication with just a click.
* **Retrieve Results**: Download the results in a nicely formatted spreadsheet. For added convenience, where supported, obtain optional links directly connecting your matches to their corresponding record views and merge functions in your CRM.

This approach ensures a hassle-free experience, helping you to efficiently clean your CRM data with ease.

Here's a simple example to start: 

https://colab.research.google.com/github/benevolent-machines/crm-deduper/blob/main/docs/examples/simple.ipynb

