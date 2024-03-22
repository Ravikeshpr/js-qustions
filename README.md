# js-qustions
output based interview questions and answers

#########################
1. Find repetations of chars in a string using reduce funtion in jS

 const str = "jhkggffjkhkjhkhgjf"

const strArr = str.split("");


const val = strArr.reduce((ac,item)=>{
  
  if(!ac[item]){
    ac[item]= 1;
  } else{
   ac[item] = ++ac[item]
  }
  return ac;
  
},{});


console.log(val)

==============================
Ans:
{"j":4,"h":4,"k":4,"g":3,"f":3}
=============================

2. ===========================================================================================
Question:   Write a funtion to flaten a deep object.

Ans:
  
// Declare an object
let ob = {
    Company: "GeeksforGeeks",
    Address: "Noida",
    contact: +91-999999999,
    mentor: {
        HTML: "GFG",
        CSS: "GFG",
        JavaScript: {
            node:"React"
        }
    }
};
 
// Declare a flatten function that takes 
// object as parameter and returns the 
// flatten object
const flattenObj = (ob) => {
 
    // The object which contains the
    // final result
    let result = {};
 
    // loop through the object "ob"
    for (const i in ob) {
 
        // We check the type of the i using
        // typeof() function and recursively
        // call the function again
        if ((typeof ob[i]) === 'object' && !Array.isArray(ob[i])) {
            const temp = flattenObj(ob[i]);
            for (const j in temp) {
 
                // Store temp in result
                result[i + '.' + j] = temp[j];
            }
        }
 
        // Else store ob[i] in result directly
        else {
            result[i] = ob[i];
        }
    }
    return result;
};
 
console.log(flattenObj(ob));
//output

{
    "Company": "GeeksforGeeks",
    "Address": "Noida",
    "contact": -999999908,
    "mentor.HTML": "GFG",
    "mentor.CSS": "GFG",
    "mentor.JavaScript.node": "React"
}


==============================================================================================

4. =============================================================================================
Strings in javascript are immutable or not?

Ans:

Just to clarify for simple minds like mine (from MDN):

Immutables are the objects whose state cannot be changed once the object is created.

String and Numbers are Immutable.

Immutable means that:

You can make a variable name point to a new value, but the previous value is still held in memory. Hence the need for garbage collection.

var immutableString = "Hello";

// In the above code, a new object with string value is created.

immutableString = immutableString + "World";

// We are now appending "World" to the existing value.

This looks like we're mutating the string 'immutableString', but we're not. Instead:

On appending the "immutableString" with a string value, following events occur:

Existing value of "immutableString" is retrieved
"World" is appended to the existing value of "immutableString"
The resultant value is then allocated to a new block of memory
"immutableString" object now points to the newly created memory space
Previously created memory space is now available for garbage collection.

=============================================================================================================================================


TIMER Stop


import { useState, useEffect, useRef } from "react";
import Counter from "./Counter";
import "./styles.css";
let interval;
export default function App() {
  const [timer, setTimer] = useState(0);
  const [state, setState] = useState(0);
  const increment = useRef(null);
  const decrement = useRef(null);
  const handleStart = () => {
    console.log("timer and state", timer, state);
    if (state > timer) {
      increment.current = setInterval(function () {
        setTimer((timer) => timer + 1);
      }, 1000);
    }
    if (timer > state) {
      decrement.current = setInterval(function () {
        setTimer((timer) => timer - 1);
      }, 1000);
    }
  };

  useEffect(() => {
    console.log("fff", state, timer);

    if (state == timer || timer <= 0 || timer >= 10) {
      clearInterval(increment.current);
      clearInterval(decrement.current);
    }
  }, [state, timer]);

  const handleReset = () => {
    clearInterval(increment.current);
    setTimer(0);
  };

  return (
    <div className="App">
      <p>Timer: {timer}</p>
      <input value={state} onChange={(e) => setState(e.target.value)} />
      <button onClick={handleStart}>Start</button>
      <button onClick={handleReset}>Reset</button>
    </div>
  );
}



