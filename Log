import React, { useState, useEffect } from "react";
import { BrowserRouter as Router, Switch, Route, Link } from "react-router-dom";
import Login from "./Login";
import Dashboard from "./Dashboard";
const App = () => {
  const [username, setUsername] = useState("");
  useEffect(() => {
    const token = localStorage.getItem("token");
    if (token) {
      setUsername(token);
    }
  }, []);
  return (
    <Router>
      <div>
        <nav>
          <Link to="/login">Login</Link>
          <Link to="/dashboard">Dashboard</Link>
          {username && <span>Welcome, {username}</span>}
        </nav>
        <Switch>
          <Route path="/login">
            <Login setUsername={setUsername} />
          </Route>
          <Route path="/dashboard">
            <Dashboard />
          </Route>
        </Switch>
      </div>
    </Router>
  );
};
export default App;
import React, { useState, useEffect } from "react";
import axios from "axios";
const Login = ({ setUsername }) => {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const handleSubmit = async (e) => {
    e.preventDefault();
    try {
      const response = await axios.post(
        "http://afc7a104784594208b12c3474fa3c924-1060237241.us-east-2.elb.amazonaws.com:9002/login",
        {
          email,
          password,
        }
      );
      const token = response.data.token;
      localStorage.setItem("token", token);
      setUsername(token);
    } catch (error) {
      console.error(error);
    }
  };
  return (
    <div>
      <h1>Login</h1>
      <form onSubmit={handleSubmit}>
        <input
          type="email"
          placeholder="Email"
          value={email}
          onChange={(e) => setEmail(e.target
