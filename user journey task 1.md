


In this project, you are provided with data containing the user journeys of people who bought our product. You need to create Python programs to analyze the sequence of visited pages with the objective of improving the front page flow and identifying which pages are important.
But before analyzing this data, you must first clean it and prepare it for the next step.
For this part of the process, you must create a Python program with three functions to help you transform the data into a more analysis-ready state and then export this new data to a CSV.
To begin, inspect the CSV itself and see if there is any need to clean the data. After Inspection, you should notice that some user journey strings have multiple duplicate pages, one after another. While the Homepage reference in journeys like Homepage-Pricing-Homepage might be helpful for the analysis, the repeating reference in Homepage-Homepage-Homepage-Pricing is not.

The first function you need to create removes sequences of repeating pages. It should leave just a single entity in the place of the sequence. But it should only apply where the duplicate page is replicated sequentially. So, it should do nothing in the first example (Homepage-Pricing-Homepage) while replacing the second (Homepage-Homepage-Homepage-Pricing) with Homepage-Pricing. This operation should be done for each row of data.
The function details are as follows:
Example name: remove_page_duplicates
Input parameters:
data - the dataframe containing all the data
target_column - the name of the column containing the user journey strings (default is 'user_journey')
Output: It should return a new dataframe with the cleaned-up journey strings. It should not modify the original dataframe.

Next, look at the structure of the data. Currently, there is a row for every session of the user. But when considering a user's journey, we're interested in the page sequences instead of the specific sessions. To prepare the data for the analysis, you'll need to group a single user's journey strings into one big string-which is what the second function will do.
Make the function as general as possible-grouping all the sessions will not suffice. What if we later decide that we want to consider just the first 10 sessions or the last 3? This is a component you need to add to this function, possibly achieved in many ways. Below, you can find one possible implementation.
The function details are as follows:
Example name: group_by
Input parameters:
data - the dataframe containing all the data
group_column - the name of the column which we want to group into a single record (default is 'user_id')
target_column - the name of the column containing the strings (default is 'user_journey')
sessions - the number of sessions to group; if it's the string 'All', consider all sessions (default is 'All')
count_from- either 'first'; or 'last'; indicates what to group if the session parameter is an integer-e.g., if sessions is 10 and count_from is 'last', the function should group only the last 10 sessions (the grouping order should still remain the same from the earliest to latest session) (default is 'last')
Output: The function should return a new dataframe that contains the grouped strings. It should not modify the supplied one.

