# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

<img width="502" alt="Assignment_1 - ERD 1 (Type 1 SCD)" src="https://github.com/user-attachments/assets/52547eb0-746c-46ed-87c5-8f8f21827882">

<img width="483" alt="Assignment_1 - ERD 2 (Type 2 SCD)" src="https://github.com/user-attachments/assets/6f3d1d99-892d-4d44-9d88-fb3a6af88f8f">

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.
# I included shift_start_time and shift_end_time to the Employee_Shift table on ERD 1 and 2 above.  You would be able to use this information to set up a morning shift (for example from 8:00AM to 12:00PM) and an evening shift (4:00PM to 9:00PM)

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Your answer...
ERD 1 above was created using Type 1 SCD. As such, if information already exists for customer_ship_address, it will be updated with the new information (overwritten).  There would be no duplicate customer shipping addresses in the table and that the information reflects the most recent current information
ERD 2 above was created using Type 2 SCD (with cust_ship_address_start_date and cust_ship_address_end_date).  As such, it will retain and track historical changes (historical data will be maintained by adding a new row when the customer shipping address changes)
There are privacy implications if we are storing historical customer shipping addresses that are not be utilized.  If that is the case it would go against CASL legislation in Canada and GDPR in the UK.

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
Your answer...
Two key differences:
The AdventureWorks schema is a lot more precise and detailed compared to what I provided.  In particular:
i.  Sales section - provides a lot of relevant information such as currency, sales tax and credit card.
ii.  Product section - provides a far better description of the actual product including reviews, illustrations/ photos, category, sub-category and culture
iii. Special offers are tracked in the sales section
For all three outlined above, the key benefit would be a far more robust analysis of sales (for example, the sales lift on the special offers versus regular price) and understanding what product segments are driving sales (category/ sub-category/ culture), perhaps there would be some seasonality in sales that could be better understood as well.

Secondly, the AdventureWorks schema provides a far more holistic view of work order processing and inventory management.  This schema would do a better job of tracking the inventory but also understanding where various orders reside in the work order process at a much more granular level than I provided in my schema.  They would have more timely inventory management to order more units before they go out of stock or perhaps discount a book if they have too many in stock.  They would also be better able to pinpoint any bottlenecks/ delays in the work order process, if there are any delays in orders getting filled.


What I would change:
I would make the changes above to include far more detail to better flesh out the actual process.  I would prefer the type of data that would get captured in the AdventureWorks schema that would enable a far more robust analysis of sales, inventory and work flow process.  It would provide the granular level of information that would be required to get to the bottom of an issue (whereas my approach was far to topline without the granularity required).  I would also have included the TransactionHistoryArchive table that is not connected to any of the other tables (ensuring limited access for sales analytics year over year)

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `September 28, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-4-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
