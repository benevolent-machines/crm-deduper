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

### How to Use the `run` Function

The `run` function is the core of our deduplication tool, designed to be both powerful and easy to use. Here's a step-by-step guide on how to use it:

1. **Prepare Your Data**: Ensure your data is in a supported format (xls, xlsx, csv). This data should be exported from your CRM and include the columns you wish to search for duplicates.

    ``` sql
    SELECT customer_id, first_name, last_name, address, city, state -- essential
         , total_amount, created_by, created_date  -- optional, but very helpful
    FROM customer_table
    ```
    
2. Define Your Parameters: Customize the deduplication process by specifying the parameters based on your needs. Below are key parameters explained:

    * input_data: The file or DataFrame containing your CRM data.
    * entity_id: The unique identifier for each record in your dataset.
    * search_columns: List of columns to be considered for finding duplicates (e.g., ['first_name', 'last_name', 'address', 'city', 'state']).

3. Execute the Deduplication: Call the run function with your data and parameters. For example:

    ``` python
    crm_deduper.run(
        input_data="your_data.csv",
        entity_id="customer_id",
        search_columns=['first_name', 'last_name', 'address', 'city', 'state'],
    )
    ```
Review the Results: After the process completes, examine the deduplicated data and download the results as needed.

### Household Match Exclusions
In many cases, potential matches may actually be different people residing at the same address, leading to false positives. To mitigate this:

Use the `similar_column` parameter, typically set to 'first_name', to require a degree of similarity in the first name for a match. This helps exclude common household duplicates.

### Major Amounts
Focus your deduplication efforts on records that have a significant impact by using:

`amount_column` to specify the column containing transaction or donation amounts.
amount_minimum to set a threshold, ensuring at least one of the records in a matching pair exceeds this amount.
This approach helps prioritize deduplication where it matters most, based on the financial impact.

Recent Duplicates
Addressing recent duplicates promptly can prevent issues from escalating. To isolate recent duplicates:

Use recent_column to specify the column with the record's date (e.g., insert_date).
Set recent_days to define how recent the records need to be to qualify for deduplication.
This feature enables you to focus on newly created duplicates, which may be more relevant for immediate action.

Source Auditing
Understanding the source of duplicates can inform strategies to prevent future occurrences. To isolate duplicates by source:

string_column allows you to specify the column that identifies the source (e.g., created_by).
string_equals is used to match the source column's value to a specific source you wish to audit.
This functionality is crucial for identifying and addressing the root causes of duplication, potentially leading to systemic improvements in data entry or integration processes.

By following these guidelines and utilizing the run function with the appropriate parameters, CRM users can significantly enhance their data quality, leading to improved customer relations, more effective marketing, and more accurate sales forecasting.

