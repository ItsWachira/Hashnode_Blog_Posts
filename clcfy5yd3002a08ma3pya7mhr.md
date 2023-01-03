# How to Fetch Data From the GitHub API using ReactJS

Fetching data from an external API is a common practice in building applications. In this guide, you will learn how to fetch JSON data from the GitHub REST API and render that data inside a ReactJS component by making asynchronous requests to the API.

## Approaches To Use

There are two common methods you can use to fetch data from an external API using React/JavaScript:

1.  **Fetch** - a Web API available in browsers used to fetch data.
    
2.  **Axios** - a `Promise` based HTTP client.
    

## DEMO

You will fetch data from the GitHub Users and Repos(repositories) API for a specific GitHub username and render a ReactJS component that displays the user's details, including the name, profile avatar, and some of their repositories.

To follow along, you can clone the project from this [GitHub repository](https://github.com/Wachira/github-React).

%[https://youtu.be/d-_6N3uEL2o] 

## Set Up a ReactJS Component

Open your terminal and run this command to create a new ReactJS project and spin up the ReactJS development server:

```plaintext
npx create-react-app access-api-react

cd access-api-react

npm start
```

To check if the sample React app is running, open [http://localhost:3000](http://localhost:3000) in your browser. You should see a React logo.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671522264497/ooVL8adl0.png align="center")

## Create the Main Components

Open your React project, in the `src/` directory, create a new folder, and name it `components`. This folder will house two components, a search bar and a results component which we will use to fetch data and render it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671541688287/_C6cFE_fl.jpg align="center")

In the `components` folder, create 3 new files: a `Results.js`, `SearchBar.js` file, and a `styles.css` file for styling the components.

### Fetch Data Using Axios

Open your VS Code terminal and run this command to install Axios `npm` dependency in your project.

```plaintext
npm install axios
```

Next, in your `SearchBar.js` file, add the code below:

```plaintext
import React, {useState} from "react";
import axios from "axios";
import Results from './Results';
import  "./styles.css";

const SearchBar = () => {
    const [searchInput, setSearchInput] = useState("");
    const [gitHubRepos, setGitHubRepos] = useState([]);
    const [data, setUserdata] = useState([]);

    const handleChange = (e)  => {
        setSearchInput(e.target.value);
    };

    const handleClick = async () => {

        try {
            const gitHubRepos = await axios.get(`https://api.github.com/users/${searchInput}/repos`);
            setGitHubRepos(gitHubRepos);

            const {data} = await axios.get(`https://api.github.com/users/${searchInput}`);
            setUserdata(data);


        }
        catch{
            console.log(err);
        }
    };
```

In the code above, the SearchBar component uses a `useState` hook to manage 3 states:

*   The user input - This is the GitHub username that you want to fetch.
    
*   The Repositories data fetched from GitHub API
    
*   The User data obtained from API
    

The `handleChange`function tracks changes in the input field, in turn, updates the `searchInput` state.

The `handleClick` function is called when a user presses the search button. This in turn triggers the Axios `get()` method which takes a `URL` argument (the API endpoints) and makes a `http` request to GitHub API. The function returns JSON data which is then used to update the **user data** and **repositories** states. We wrap the function in a `try` and `catch` block in order to log and debug any errors, if any.

### Fetch Data Using Fetch API

The syntax :

```plaintext
 const handlClick = async () => {
    
        try {
            const response = await fetch(`https://api.github.com/users/${searchInput}`);
            var data = await response.json();
            setUserdata(data);

        }
        catch{
            console.log(err);
        }   
    };;
```

This method is almost similar to using Axios. However, the only difference is that you have to serialize the API response to **JSON** format before updating the states.

The search bar component returns a `div` with the `search input field` and renders the `results` component. Data from the `data` and `GitHub repositories` **states** are passed as `props` to the `results` component.

```plaintext
return (
        <div>
        <div className="github">
        <h1> Github Data</h1>
        <input className="input" type="text" 
        placeholder="Search"  
        value={searchInput} 
        onChange={handleChange}/>
        <button onClick={handleClick}>Search</button>
        </div>

        <div > 
                <Results 
                Repos={gitHubRepos}
                UserData={data}
                />
        </div>
       
        
        </div>
    );
    }

    export default SearchBar;
```

### Results Component

Once the user information and repository data have been fetched, they are passed as props from the `searchBar` component. The repositories data is wrapped in an array while the user data -- in an object. The map function comes in handy in mapping through each repository in the array and rendering them as an individual list item.

```plaintext
import React  from "react";
import  "./styles.css";

const Results = (props) => {
    const {Repos} = props;
    const {UserData} = props;
 
    const userRepos = Repos.length !==0 ? 
    (Repos.data.slice(0,5).map((item) => <li key= {item.id}> {item.name} </li> ) ) : (<li></li>);


    return (

        <div className="results">
        <div className="userName"> Name: {  UserData["name"]}</div>
        <div className="ProfilePic"> <span>Profile Picture </span>  <img src={UserData["avatar_url"]} /> </div>
        <h2> Top Repositories</h2>
        <ul>{userRepos}  </ul>
        </div>
    );
    }

    export default Results;
```

## Wrapping Up

Both `Axios` and `fetch` achieve the same goal, you can use either to fetch data from an external API.

However, note that `axios` should be added as an `npm` dependency, whereas `fetch` is available out of the box as a **web API**.