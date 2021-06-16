---
layout: page
title:  "Career Changes & WATCHMATCH"
date:   2021-06-16 12:30:00 -0400
categories: project
---
![image](/assets/img/wm-screenshot.png)

## *I am currently job hunting, as of June 2021. Please see my [resume](/resume/resume) and [get in touch](mailto:jasonchilcode@gmail.com)*

Before COVID-19 shut down the majority of film and television production (and many other industries as well) I had been working in the world of film and TV for many years. I had gone to school for writing and directing, and had been a writer, producer, director, camera assistant, production manager, wardrobe assistant, gaffer... just about every crew job on set. Short films I had written, produced, or directed had been shown in film festivals across the world, and a few of them even won awards. Most recently I ended up working as a background actor/stand-in/photo double, managing to join SAG-AFTRA and work on most of the scripted TV shows that shoot in the New York area, and some big movies, too.  

It was the industry I had spent most of my life wanting to be in, but after years of being in it, I was worn out.  The sporadic and unpredictable nature of the work was making me tired. I had been thinking about a career change that would play to one of my other great interests: computers. 

I had been very into computers since I was a kid, back before the internet boom, back when MS-DOS was still something you had to use for certain programs. I had made countless little programs in languages like LOGO and BASIC. I very briefly tried to learn C++, and later on taught myself HTML, CSS, and Flash to make websites for my films, art, and photography. 

Even before the pandemic, I had begun exploring learning Javascript on websites like FreeCodeCamp, but when film and TV production shut down indefinitely, I got even more serious and ended up enrolling in Flatiron School's Software Engineering bootcamp, which was being conducted remotely.  

Bootcamp was challenging but very fulfilling.  Ruby was completely new to me, and learning about things like RESTful conventions and MCV were revelatory to me in understanding how dynamic websites actually work. I was very impressed with the flexibility and functionality of React.js, and it was satisfying to use it along with CSS to create projects that matched the image I had in mind. The rush of new information was constant but the feeling when something finally "clicked" made it worth it.  The most rewarding thing, however, was collaborating with people of all different backgrounds and perspectives, tackling technical problems from angles that I wouldn't have initially thought of, and in general supporting one another. 

So when it came time for our first solo project, our final project, I wanted to make something that could connect people.  Drawing on my film background, where so many hours were spent discussing movies, the idea came to me of a web app that would help people find others with similar taste in film. I began looking in to what movie APIs I could get access to, and researching how dating sites made their matches. 

I was happy with what I ended up showing for the final presentation, but there were some issues I didn't have time to solve. Since I was just presenting it myself, I didn't prioritize error handling for the sign up and log in features. There was also a strange behavior on the backend where movie data would occasionally get corrupted. In the time since my time at Flatiron School ended, I have fixed these issues, and am continuing to improve the user experience and add new functionality.

WATCHMATCH is a webapp which matches users based on how they rate movies. Users can rate movies on a scale from 1/2 star to 5 stars. The ratings of all movies any two users have both rated are compared to each other on a weighted algorithmic scale and then averaged to find a maximum possible compatibility percentage of the users' tastes. In addition, the percentage is adjusted by a margin of error based on how many rated movies the users have in common. This method was inspired by the algorithm used on OKCupid. [Inside OKCupid: The math of online dating](https://www.ted.com/talks/christian_rudder_inside_okcupid_the_math_of_online_dating/transcript?language=en)

The weighted difference for any two users' ratings of the same movie are calculated as follows:

![weighted difference](/assets/img/weighted-difference.png)

Where a and b are two users' ratings of the same movie (4.5 is the greatest possible difference between two ratings.)

## Technologies Used

- React.js - The frontend of WATCHMATCH was written in React.js. This currently also includes the calculations of the matching system.
- [TMDb API](https://developers.themoviedb.org/3) - External API used for movie information and poster images, as well as searches by keyword, genre, and lists from users on their extensive website. Movies are queried by the frontend, then sent to the backend to ensure they are already in the WATCHMATCH database by checking their id from the TMDb API first, to prevent duplicate movies.
- [react-router-dom](https://www.npmjs.com/package/react-router-dom) - Used for all the routing and links.
- [react-rating-stars-component](https://www.npmjs.com/package/react-rating-stars-component) - Used for responsive, customizable ratings display and user input.
- [React Icons](https://www.npmjs.com/package/react-icons) - Social media icons on the user profile pages.
- [Bootstrap](https://getbootstrap.com) - Used to style buttons and forms.

- Ruby on Rails - The backend of WATCHMATCH was written in Rails. This includes the database migrations, routes, serializers, models, and controllers.
![model association diagram](/assets/img/wm-models.png)
The match percentages are calculated on the frontend currently.



WATCHMATCH is currently live at [https://watchmatch.herokuapp.com/](https://watchmatch.herokuapp.com/) and it's a living project, known bugs can be found as issues on [watchmatch-backend](https://github.com/jasonchilcott/watchmatch-backend) and [watchmatch-frontend](https://github.com/jasonchilcott/watchmatch-frontend). PRs are welcome.