# Udacity Completed Review Viewer

Steps to get this working:

 1. Download/clone this repository and open the index.html file or open the [live version here](https://simplydallas.github.io/udacityreviewparser/).  (live version is recommended)
 2. Open the [Udacity reviewer dashboard](https://review.udacity.com/#!/submissions/dashboard) and make sure you are logged in
 3. In the dev console (with the udacity dashboard in focus) paste the following code:

 ```javascript
 copy($.ajax({
  method: 'GET',
  url: 'https://review-api.udacity.com/api/v1/me/submissions/completed.json',
  headers: { Authorization: JSON.parse(localStorage.currentUser).token },
  async: false
}).responseJSON)
 ```
 
 4. Wait for the console to echo the word `undefined` which means your result is now in your clipboard
 5. In the webpage/tool paste the JSON into the text box
 6. If you want to start over, just refresh the page.  There is no clear function right now
 7. Your data is stored locally on your pc.  If you refresh after the first use you should see a button that says `Load locally stored data from your last visit`.  This will not pull fresh data from Udacity but it will let you see your last loaded data without getting it and pasting it again.

 ### Only the following information is actually presented.  If you would like more information it will require editing the tool.

 * review id (this is the default sort item and links to the original review)
 * date review completed
 * price associated with the review
 * result of the review (if the student left a note this will)
 * The name of the project reviewed

 note: Although that is the only information presented, the tool may find things that don't quite seem to make sense when you filter.  For example, if your student's name was Jeff and you type `jeff` into the search it will find that review but you won't be able to see the student name.  This is probably not ideal behavior but this is a quick throw together tool until udacity has their own front end so I didn't take time to present all information.

 ### Basic overall stats are shown on the navbar / header

 * Total count of reviews (dropdown menu shows total per project and %)
 * Total earned amount (dropdown menu shows total per project and %)
 * Average earned per review
 * Earliest review date
 * Most recent review date.