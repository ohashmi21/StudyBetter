<template>
    <div>
      <h1>Spaced Breaks</h1>
      <div id="container">
        <div id="options">
          <div class="tooltip">
            <span class="tooltiptext">Strategically spaced time periods between review sessions, optimizing the timing of information recall for better long-term retention.</span>
            <router-link to="/spacedBreaks/Interval" id="Interval">Interval (in progress) </router-link>
          </div>
          <div class="tooltip">
            <span class="tooltiptext">Random pauses during intense focus sessions allow the brain to idle briefly, enhancing learning by facilitating rapid neural replay and consolidation of information.</span>
            <router-link to="/spacedBreaks/random" id="random">Random</router-link>
          </div>
        </div>
        <div id="info">
          <p>
            <h2>What are spaced breaks?</h2>
            The "spaced breaks" technique is a studying technique that has been proven to improve cognitive performance. Studies have shown that taking small gaps when studying, there is a rapid replay of neurons at up to 20 times the normal speed! This replay helps consolidate information and strengthen neural connections, leading to better learning outcomes. When you incorporate spaced breaks into your study or work routine, you allow your brain to recharge and refresh. These breaks can be as simple as pausing for a couple of minutes to let your mind wander, engaging in deep breathing exercises, or taking a short walk. By incorporating spaced breaks, you optimize your cognitive function and make your learning sessions more productive. You'll experience improved focus, enhanced information retention, and increased overall efficiency.
          </p>
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
      display: grid;
      grid-template-columns: 1fr 1fr;
      column-gap: 100px;
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
  