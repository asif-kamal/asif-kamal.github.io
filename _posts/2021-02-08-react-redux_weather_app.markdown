---
layout: post
title:      "React-Redux Weather App"
date:       2021-02-08 14:34:29 -0500
permalink:  react-redux_weather_app
---


I began with creating a new rails app. The model I came up with was note, since I had an idea of allowing users to write notes in a weather-journal app. 

I focused mainly on the frontend as I needed to implement many new concepts. The most fascinating part of building my app was learning how to use Redux and Thunk with React. 

Creating a new rails app for backend API use I decided to generate a notes model with content and city as its attributes. 
For me as a visual learner I needed to see my react frontend on the browser to be able to build my app. I found the [Fullstack Article](https://www.newline.co/fullstack-react/articles/how-to-get-create-react-app-to-work-with-your-rails-api/) helpful but I had already installed http-proxy-middleware. After repeated attempts to have the proxy middleware connect my backend to my frontend, I opted for foreman.  

Now building a react app was the next step. As I built each component I learned about using data from openweathermap and rendering cards for each day of the week. I alos learned that Thunk middleware exists because fetch requests are asychronous and we need an action to be dispatched while the state is being updated.

I in turn created an action creator to fetch data from the openweathermap api. Passing that as props to my WeeklyForecastContainer I rendered a child component called DayForecastContainer. 

For my NotesForm and NotesList components I used the react hook, useState. I also used the react hook useEffect. This caused an error in my fetch post request. Since useEffect continuously rerenders after the component mounts I had to add an empty array for it to check against and stop rerendering.

My NotesList component currently looks like this:

![using useState React Hook](https://pasteboard.co/db2ce88d-8cc3-4a4a-9207-9ba28dfd1c1e)


I do see why redux is useful as it keeps all our data in one place, in the state. I plan to create new action creators and a reducer for setting notes instead of using useState. 

```
const initialState = {

    notes: [],

}


export const notesReducer = (state = initialState, action) => {
switch(action.type){
    case "SET_NOTES": 
        return {...state, notes: action.payload.notes} 
    default: 
        return {...state}
}

}


```

```
export const getNotes = () => {
        const config = {
            method: "POST",
            headers: {
                "Content-Type": "application/json",
                "Accept": "application/json",
            },
        body: JSON.stringify({
            note:{
                content: note.content,
                city: note.city
            }
        }),
    
		return dispatch => {

    fetch('/api/v1/notes', config).then(res=>(res.json())
    .then(notes => {
		dispatch({
		type: "SET_NOTES",
		payload: {notes,
		}
		})
		})
		}
		
		
};
    
    setNotes([...notes, note]);
    };
```

My final project was difficult to build, but it taught me how redux works and I am ready to keep building new apps with what I have learned.



