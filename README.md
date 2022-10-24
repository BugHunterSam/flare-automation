# flare-automation
This is the code submitted as part of the take home exercise for a quality engineer role at Flare. [Here is the exercise PDF](https://drive.google.com/file/d/1g2idw-NrrHw8LjrnfASydcxWSTQtI5lL/view?usp=sharing).

The exercise involves building out some API automation for [CatAPI](https://thecatapi.com/), you can checkout the [the documentation here](https://developers.thecatapi.com/view-account/ylX4blBYT9FaoVd6OhvR?report=aZyiLrsCh#tag/Favourites). I've chosen to use postman.

# SetUp
[Install postman](https://www.postman.com/downloads/) or use the browser version
Clone this repo `git clone https://github.com/BugHunterSam/flare-automation.git`
Import the [postman collection](https://github.com/BugHunterSam/flare-automation/blob/main/Flare%20Automation%20task.postman_collection.json) and the [test environment collection](https://github.com/BugHunterSam/flare-automation/blob/main/TheCatAPI%20-%20Live.postman_environment.json)

You should see a view that looks like:
![a diagram showing what the postman UI looks like](https://bughuntersam.com/wp-content/uploads/2022/10/postman.png "explaining the postman UI")
1. This is where the collection that you imported will be
2. This is the request that is being tested, you can select a request from the collection to see this
3. if you navigate to the tests tab you should be able to see the test for each request
4. I can't count and missed this one 😂
5. hitting send should show the response, body and tests results down here
6. Here is where the test environment variables that you imported will be

I found [the postman documentation](https://learning.postman.com/docs/writing-scripts/script-references/postman-sandbox-api-reference/) to be helpful for this exercise.

# Feedback
This excersice took a good 1.5 days of effort to complete. There were issues with getting the API keys to work, I thought there was a bug with the `POST favourites` request when using an API key. I was getting an empty payload. So this lead me to explore the `upload images` request to see if I could figure out how an image id was added. Turns out I didn't need to do this and it wasted 4 hours of investigation and exploration effort.

I spent half a day exploring the postman API docs and stackoverflow questions figuring out how to get my assertions to work. Javascript can be a little frustrating to work with. It's probably 2 hours of effort just to write this documentation.

I've left some refactor notes in my tests. In the spirit of time I didn't want to spend the extra effort polishing them when I've already done this much. I would add a few prescript steps to ensure every API test can be run independantly no matter how it's run. For example as part of a CI/CD pipeline or a performance load test.

From doing this testing I think there are some design flaws with the APIs around error scenario's that can be improved. For example attempting to delete a favourite that doesn't exist should result in a 404 not found, rather than a bad request.

The `POST https://docs.thecatapi.com/favourites` in the PDF had the wrong URL, it should be `POST https://docs.thecatapi.com/v1/favourites`

If the goal was to prove:

* Ability to go through an API documentation and understand how it works ([blog:testing an API I built myself](https://bughuntersam.com/performance-testing-apis-with-async-awaits/))

* Ability to write automated API tests that work consistently ([video: live coding for automation](https://www.youtube.com/watch?v=kstbRRnrX1U))

* Ability to work with code versioning (Git) (my repo's are here aren't they?).

I could have proven this without spending 1.5 days on this task.
