Summary of Changes

  I focused on fixing the highest-impact issues that affected correctness, performance, and user experience instead of making large architectural changes.

>  Backend
1. Fixed the SQL search query by adding parentheses so the status filter is applied correctly.
2. Removed the artificial Thread.sleep() delay that slowed every API request.
3. Added validation for invalid status values to prevent server errors.
4. Reviewed the pagination logic and identified that server-side pagination would be a better     
   long-term solution.

>  Frontend
1. Fixed the loading state so it always resets after an API request, even when the request fails.
2. Cleared previous error messages before sending a new request.
3. Reset the page number when the search text or status filter changes.
4. Improved API error handling by displaying more meaningful error messages.

>  What I Chose Not to Change and Why
1. I did not refactor the project into additional service layers because the assignment was time-boxed 
   and the existing structure was sufficient after fixing the major issues.
2. I did not replace the manual pagination with Spring Data Pageable because it would require larger 
   changes to the repository, controller, and frontend response handling. Instead, I documented it as 
   an important improvement.
3. I did not add features such as search debouncing, caching, authentication, or UI redesign because 
   they were outside the scope of fixing the highest-value bugs.

>  Biggest Remaining Risk
   The biggest remaining risk is that pagination is still performed in memory after fetching all 
   matching records from the database. This approach works for small datasets but does not scale well 
   as the number of tasks increases. Using database-level pagination (Pageable) would significantly 
   improve performance and memory usage.

   Another improvement would be introducing proper logging and centralized exception handling instead 
   of handling errors directly inside the controller.

>  Tools / AI Used

   I used ChatGPTand claude to review the code, discuss different implementation options, and improve
   the quality of my fixes. I verified each suggested change by reading the code and ensuring I
   understood the root cause before applying it.

   All handwritten explanations were prepared based on my understanding of the implemented fixes.