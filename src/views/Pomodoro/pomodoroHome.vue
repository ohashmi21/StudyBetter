<template>
    <div>
      <h1>Pomodoro</h1>
      <div id="container">
        <div id="options">
          <div class="tooltip">
            <router-link to="/pomodoro/timer" id="timer">Pomodoro</router-link>
          </div>
        </div>
        <div id="info">
          <p>
            <h2>What is the Pomodoro technique?</h2>
            The Pomodoro Technique, developed by Francesco Cirillo, is a time management method that involves breaking work into intervals, typically 25 minutes long, called "Pomodoros." During each Pomodoro, individuals focus exclusively on a chosen task, aiming to eliminate distractions. After completing a Pomodoro, a short break of 5 minutes is taken, and after four cycles, a longer break of 15–30 minutes is recommended. The structured approach helps improve concentration, productivity, and time management by creating a sense of urgency and preventing burnout.          </p>
        </div>
      </div>
    </div>
    
  </template>
  
  <style>
    body {
      background-color: black;
    }
    
    h1 {
      color: white;
    }
    
    a {
      color: white;
    }
    
    #options {
        text-align: center;
    }
    
    #container {
      margin-right: 10%;
      margin-left: 10%;
    }
    
    #interval {
      margin-right: 10%;
    }
    
    #info {
      margin-top: 30px;
      color: white;
      font-size: 2.5vh;
    }
    
    .tooltip {
      position: relative;
      display: inline-block;
      border-bottom: 1px dotted black; /* If you want dots under the hoverable text */
    }
    
    /* Tooltip text */
    .tooltip .tooltiptext {
      visibility: hidden;
      background-color: black;
      color: #fff;
      text-align: center;
      padding: 5px 0;
      border-radius: 6px;
      top: 100%;
      left: 50%;
      margin-left: -60px;
      /* Position the tooltip text - see examples below! */
      position: absolute;
      z-index: 1;
      font-size: 2.5vh;
      width: 100%;
    }
    
    /* Show the tooltip text when you mouse over the tooltip container */
    .tooltip:hover .tooltiptext {
      visibility: visible;
    }
  </style>
  