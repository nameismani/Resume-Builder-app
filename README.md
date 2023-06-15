# Resume-Builder-app

"Hello, I wanted to apologize for the delay in submitting the completed task. Over the past two days, I have been quite busy. As I am currently in the learning stage, I put forth my best effort to develop the Resume Builder app. Throughout the development process, I learned a lot and I'm grateful for the opportunity you gave me. In this project, I decided not to use Bootstrap because I believed I could create a better app using CSS alone. This allowed me to gain more experience with CSS styling. Additionally, I learned about the 'react-tag-input' library and its implementation in the app.

I must admit that I have only completed around 60% of the task and I am unsure about the intended functionality of the app after clicking the submit button. It seems like there should be some action or behavior associated with it, such as saving the resume data or navigating to another page. To accomplish seamless navigation within the app without causing a full page reload, React Router can be 
I am tried to host the web page using git hub byt i donkow how to hsot that. I will learn soon hwo to host react app in github. so i am added the code in this readm me and i am adding image of the site if it is possbile

Once again, I appreciate the opportunity and I apologize for not completing the entire task. If you have any further instructions or need assistance with specific aspects of the project, please let me know. Thank you."


-------------------------------------------------------- App.js file code -------------------------------------------------------------------------------------------------------

import { Routes, Route, Link } from "react-router-dom";
import "./App.css";
import Home from "./Home";
import CreateResume from "./CreateResume";
import ViewResume from "./ViewResume";

function App() {
  return (
    <div>
      <nav>
        <h2 className="logo">Resume</h2>
        <ul>
          <li>
            <Link to="/" className="link">
              Home
            </Link>
          </li>

          <li>
            <Link to="/create" className="link">
              Create Resume
            </Link>
          </li>

          <li>
            <Link to="/view" className="link">
              View Resume
            </Link>
          </li>
        </ul>
      </nav>
      <div className="container">
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/create" element={<CreateResume />} />
          <Route path="/view" element={<ViewResume />} />
        </Routes>
      </div>
    </div>
  );
}

export default App;

-----------------------------------------------------------------App.css file code ---------------------------------------------------------------------------------------------------

.container {
  max-width: 800px;
  margin: 0 auto;
  height: 100vh;
  padding: 20px;
}
h1 {
  text-align: center;
  margin-bottom: 2rem;
}
body {
  background-color: aliceblue;
}
form {
  /* padding: 1rem; */
  background-color: #fff;
  border-radius: 5px;
  padding: 1rem;
}
form * {
  margin: 5px;
  width: 100%;
}

/* label {
  margin-bottom: 10px;
  margin-right: 1rem;
} */

input {
  padding: 5px 10px;
  font-size: 10px;
  border: 1px solid gainsboro;
  border-radius: 5px;
  margin-top: 5px;
  margin-bottom: 10px;
  width: 90%;
}

button {
  padding: 5px 10px;
  background-color: royalblue;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: orange;
  padding: 0.8rem;
  margin-top: 1rem;
}
ul {
  flex: 1;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  list-style-type: none;
  margin-right: 2rem;
}

ul .link {
  text-decoration: none;
  margin: 0.5rem;
  color: #fff;
  padding: 0.4rem;
}

ul .link:hover {
  background: greenyellow;
  border-radius: 10px;
}

.logo {
  font-weight: 700;
  font-style: italic;
  font-size: 16px;
  letter-spacing: 0.2rem;
  color: #fff;
  margin-left: 2rem;
  cursor: pointer;
}

.flex {
  display: flex;
}

.flex button {
  flex-basis: 300px;
  font-size: 8px;
}

.remove {
  background-color: red;
}
.rti--container {
  width: 90%;
  display: flex;
  flex-wrap: wrap;
}

.rti--tag {
  display: flex;
  width: 20%;
}
/* .rti--container * {
  background-color: red;
} */

.rti--input {
  width: 20%;
}

.rti--tag button {
  width: 30px;
}

span {
  font-size: 16px;
  font-weight: 500;
  font-style: italic;
  color: darkorange;
}
-------------------------------------------------------------------------------Home.js file code ----------------------------------------------------------------------------------
const Home = () => {
  return <h1>Welcome to the Resume Builder</h1>;
};

export default Home;
---------------------------------------------------CreateResume.js file code----------------------------------------------------------------------------------------------------

import { useState } from "react";
import { TagsInput } from "react-tag-input-component";

const CreateResume = () => {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");
  const [address, setAddress] = useState("");
  const [phone, setPhone] = useState("");
  const [education, setEducation] = useState([
    { institute: "", year: "", degree: "" },
  ]);
  const [experience, setExperience] = useState([
    { company: "", year: "", designation: "" },
  ]);

  const [skills, setSkills] = useState([]);

  const handleNameChange = (event) => {
    setName(event.target.value);
  };

  const handleEmailChange = (event) => {
    setEmail(event.target.value);
  };

  const handleAddressChange = (event) => {
    setAddress(event.target.value);
  };

  const handlePhoneChange = (event) => {
    setPhone(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    // Want to write the code what to happen after submit the form
  };

  const handleEducationChange = (index, field, value) => {
    const updatedEducation = [...education];
    updatedEducation[index][field] = value;
    setEducation(updatedEducation);
  };

  const handleAddEducation = () => {
    setEducation([...education, { institute: "", year: "", degree: "" }]);
  };
  const handleRemove = (index) => {
    const list = [...education];
    list.splice(index, 1);
    setEducation(list);
  };
  const handleRemoveExp = (index) => {
    const list = [...experience];
    list.splice(index, 1);
    setExperience(list);
  };

  const handleExperienceChange = (index, field, value) => {
    const updatedExperience = [...experience];
    updatedExperience[index][field] = value;
    setExperience(updatedExperience);
  };

  const handleAddExperience = () => {
    setExperience([...experience, { company: "", year: "", designation: "" }]);
  };

  //   const handleSkillsChange = (newSkills) => {
  //     setSkills(newSkills);
  //   };
  return (
    <div>
      <h1>Create Resume</h1>
      <form onSubmit={handleSubmit}>
        <div>
          <input
            type="text"
            placeholder="Enter your name"
            value={name}
            onChange={handleNameChange}
            name
          />
        </div>

        <div>
          <input
            type="email"
            placeholder="Enter your Email"
            value={email}
            onChange={handleEmailChange}
            name="email"
          />
        </div>

        <div>
          <input
            type="text"
            placeholder="Enter your address"
            value={address}
            onChange={handleAddressChange}
            name="address"
          />
        </div>
        <div>
          <input
            type="text"
            placeholder="Enter your number"
            value={phone}
            onChange={handlePhoneChange}
            name="phone"
          />
        </div>

        {education.map((edu, index) => (
          <div key={index}>
            <div className="flex">
              <input
                type="text"
                id={`institute-${index}`}
                placeholder="Institute"
                value={edu.institute}
                name="institute"
                onChange={(e) =>
                  handleEducationChange(index, "institute", e.target.value)
                }
              />

              <input
                type="text"
                id={`year-${index}`}
                placeholder="Year"
                name="year"
                value={edu.year}
                onChange={(e) =>
                  handleEducationChange(index, "year", e.target.value)
                }
              />

              <input
                type="text"
                id={`Degree-${index}`}
                placeholder="Degree"
                value={edu.degree}
                name="degree"
                onChange={(e) =>
                  handleEducationChange(index, "degree", e.target.value)
                }
              />
              <button type="button" onClick={handleAddEducation}>
                Add
              </button>
              <button type="button" className="remove" onClick={handleRemove}>
                Remove
              </button>
            </div>
          </div>
        ))}

        {experience.map((exp, index) => (
          <div key={index}>
            <div className="flex">
              <input
                type="text"
                id={`company-${index}`}
                value={exp.company}
                placeholder="Company"
                name="company"
                onChange={(e) =>
                  handleExperienceChange(index, "company", e.target.value)
                }
              />

              <input
                type="text"
                id={`year-${index}`}
                value={exp.year}
                placeholder="Year"
                name="experience year"
                onChange={(e) =>
                  handleExperienceChange(index, "year", e.target.value)
                }
              />
              <input
                type="text"
                id={`year-${index}`}
                value={exp.designation}
                placeholder="Designation"
                name="designation"
                onChange={(e) =>
                  handleExperienceChange(index, "designation", e.target.value)
                }
              />
              <button type="button" onClick={handleAddExperience}>
                Add
              </button>
              <button
                type="button"
                className="remove"
                onClick={handleRemoveExp}
              >
                Remove
              </button>
            </div>
          </div>
        ))}

        <div>
          <TagsInput
            value={skills}
            // onChange={handleSkillsChange}
            className="tags"
            placeHolder="Add skills..."
          />
        </div>
        <button type="submit">Submit</button>
      </form>
    </div>
  );
};
export default CreateResume;
--------------------------------------------------------------------------------------View Resume file code------------------------------------------------------------------------

const ViewResume = () => {
  return <h1>View Resume</h1>;
};

export default ViewResume;
----------------------------------------------------------------------index.js file code--------------------------------------------------------------------------------------

import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";
import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);

-----------------------------------------------------------------------------index.css file code--------------------------------------------------------------------------------------------------
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, "Courier New",
    monospace;
}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I will try to attache image of the app in this repo!

![Screenshot (62)](https://github.com/nameismani/Resume-Builder-app/assets/120552594/78752eba-8817-4796-ae11-7165f085e1e4)
![Screenshot (60)](https://github.com/nameismani/Resume-Builder-app/assets/120552594/069b0fa3-016e-495b-b9fe-8b0dcfa9fd79)
![Screenshot (61)](https://github.com/nameismani/Resume-Builder-app/assets/120552594/03e69cd8-d5b2-4eac-9da3-17be6324ecec)

