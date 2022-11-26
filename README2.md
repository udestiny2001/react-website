How to create a multi-page website using React.js ?
Difficulty Level : Easy
Last Updated : 06 Jan, 2022
Read
Courses@Sale
Discuss
Practice
Video

In this article, we will see how to create a simple multipage website using React Js.

Prerequisite:

npm
create-react-app
react-router-dom
styled components
Approach: We will create a simple website that will have different pages and a navbar. We will create multiple pages Home page, About page, Blog page, Signup page, and Contact page and then we will see how to navigate between those pages. We will be using the following packages and components:

react-router-dom: react-router-dom is a reactJS package, It enables you to implement dynamic routing in a web page.
BrowserRouter: It uses the HTML5 history API to keep the UI in sync with the URL.
Route: Its responsibility is to render UI when its path matches the current URL.
Switch: It renders the first child Route or Redirects that matches the location.
Styled-components: Styled-component Module allows us to write CSS within JavaScript in a very modular and reusable way in React.
Below is the step by step implementation:


Step 1: We will start a new project using create-react-app so open your terminal and type:

npx create-react-app react-website
Step 2: Now go to your folder by typing the given command in the terminal:

cd react-website
Step 3: Install the dependencies required in this project by typing the given command in the terminal.

npm install react-router-dom 
npm install --save styled-components
Step 4: Now create the components folder in src then go to the components folder and create a new folder name Navbar.In Navbar folder create two files index,js and NavbarElements.js. Create one more folder in src name pages and in pages create files name about.js, blogs.js, index.js, signup.js, contact.js

Project Structure: The project structure will look like the following:



Step 5: Now we will create the navbar and style it.

import React from "react";
import { Nav, NavLink, NavMenu } 
    from "./NavbarElements";
  
const Navbar = () => {
  return (
    <>
      <Nav>
        <NavMenu>
          <NavLink to="/about" activeStyle>
            About
          </NavLink>
          <NavLink to="/contact" activeStyle>
            Contact Us
          </NavLink>
          <NavLink to="/blogs" activeStyle>
            Blogs
          </NavLink>
          <NavLink to="/sign-up" activeStyle>
            Sign Up
          </NavLink>
        </NavMenu>
      </Nav>
    </>
  );
};
  
export default Navbar;
 


import { FaBars } from "react-icons/fa";
import { NavLink as Link } from "react-router-dom";
import styled from "styled-components";
  
export const Nav = styled.nav`
  background: #ffb3ff;
  height: 85px;
  display: flex;
  justify-content: space-between;
  padding: 0.2rem calc((100vw - 1000px) / 2);
  z-index: 12;
`;
  
export const NavLink = styled(Link)`
  color: #808080;
  display: flex;
  align-items: center;
  text-decoration: none;
  padding: 0 1rem;
  height: 100%;
  cursor: pointer;
  &.active {
    color: #4d4dff;
  }
`;
  
export const Bars = styled(FaBars)`
  display: none;
  color: #808080;
  @media screen and (max-width: 768px) {
    display: block;
    position: absolute;
    top: 0;
    right: 0;
    transform: translate(-100%, 75%);
    font-size: 1.8rem;
    cursor: pointer;
  }
`;
  
export const NavMenu = styled.div`
  display: flex;
  align-items: center;
  margin-right: -24px;
  /* Second Nav */
  /* margin-right: 24px; */
  /* Third Nav */
  /* width: 100vw;
white-space: nowrap; */
  @media screen and (max-width: 768px) {
    display: none;
  }
`;
Step 6: Now we will edit various pages in the project in src/pages.

import React from "react";
  
const About = () => {
  return (
    <div>
      <h1>
        GeeksforGeeks is a Computer 
        Science portal for geeks.
      </h1>
    </div>
  );
};
  
export default About;
import React from 'react';
  
const Blogs = () => {
  return (
    <h1>You can write your blogs!</h1>
  );
};
  
export default Blogs;
import React from 'react';
  
const Home = () => {
  return (
    <div>
      <h1>Welcome to GeeksforGeeks</h1>
    </div>
  );
};
  
export default Home;
import React from 'react';
  
const SignUp = () => {
  return (
    <div>
      <h1>Sign Up Successful</h1>
    </div>
  );
};
  
export default SignUp;
import React from 'react';
  
const Contact = () => {
  return (
    <div>
      <h1>Mail us on feedback@geeksforgeeks.org</h1>
    </div>
  );
};
  
export default Contact;
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
  
ReactDOM.render(
<React.StrictMode>
    <App />
</React.StrictMode>,
document.getElementById('root')
);
import React from 'react';
import './App.css';
import Navbar from './components/Navbar';
import { BrowserRouter as Router, Routes, Route}
    from 'react-router-dom';
import Home from './pages';
import About from './pages/about';
import Blogs from './pages/blogs';
import SignUp from './pages/signup';
import Contact from './pages/contact';
  
function App() {
return (
    <Router>
    <Navbar />
    <Routes>
        <Route exact path='/' exact element={<Home />} />
        <Route path='/about' element={<About/>} />
        <Route path='/contact' element={<Contact/>} />
        <Route path='/blogs' element={<Blogs/>} />
        <Route path='/sign-up' element={<SignUp/>} />
    </Routes>
    </Router>
);
}
  
export default App;
Step to run the application: Now to run the above code open the terminal and type the following command.

npm start