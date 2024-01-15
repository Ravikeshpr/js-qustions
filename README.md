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


########################
