# 🇳🇬 Nigeria States and LGAs Drop-Down

This project provides a ready-to-use drop-down structure of all 36 Nigerian states and their corresponding Local Government Areas (LGAs), perfect for forms, web apps, and admin dashboards.

## 📦 Features

- Complete list of Nigeria’s 36 states and FCT
- Over 774 LGAs mapped correctly to each state
- Easy to integrate into HTML, JavaScript, PHP, or frameworks (e.g., Laravel, React)
- Lightweight and beginner-friendly

## 🚀 Usage

Include the JavaScript or JSON file, then populate your `<select>` elements dynamically. PHP array and JSON formats available.

## 📂 Formats

- JSON

## ✅ Example

```html
<select id="state"></select>
<select id="lga"></select>
<script>
    let lga=document.getElementById("lga");
    lga.disabled=true;
    let state=document.getElementById("state");
   
    
    let y={};
    fetch("nigeria-state-lga.json")
    .then(response=>response.json())
    .then(data=>{
        y=data;
        

 //populate the state
    Object.keys(y).forEach(function (index){
    let ct=document.createElement("option");
    
    ct.text=index;
    ct.value=index;
    state.add(ct);
    
          
    });
     });
    
    
  //populate the lga
    state.addEventListener("change",() =>{
    
    let selectedState=state.value;
    console.log(selectedState);
   
   lga.disabled=false;
   lga.innerHTML="";
   
  if(y[selectedState]==undefined){
  lga.disabled=true;
      lga.innerHTML='<option value="">--Select Lga--</option>';
  }else{
  y[selectedState].sort();
       y[selectedState].forEach(function (index){
    let ctt=document.createElement("option");
    ctt.text=index;
    ctt.value=index;
    lga.add(ctt);
     
    });
    
    }
    
   })
    
    
</script>