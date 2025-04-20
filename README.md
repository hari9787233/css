Q1>Responsive Multi-Column Form with Flexbox by Using HTML and CSS
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body{
            font-family: sans-serif;
            margin:20px;
            background:#f8f8f8;
        }

        form{
            background:#fff;
            padding:20px;
            border-radius:8px;
            max-width:800px;
            margin:auto;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        fieldset{
            border:name;
            padding:0;
            margin:0 0 20px 0;
        }

        legend{
            font-size:1.2em;
            font-weight:bold;
            margin-bottom:10px;
        }
        .form-row{
            display:flex;
            flex-wrap:wrap;
            gap:20px;
        }
        .form-group{
            flex:1 1 300px;
            display:flex;
            flex-direction:column;
        }
        label{
            margin-bottom:6px;
            font-weight:500;
        }
        input,select,textarea{
            padding:8px;
            border:1px solid #ccc;
            border-radius:4px;
            font-size:1em;
        }
        .error{
            color:red;
            font-size:0.9em;
            margin-top:4px;
        }
        @media (max-width:600px){
            .form-row{
                flex-direction:column;
            }
        }
        button{
            padding:10px 20px;
            font-size:1em;
            background-color:#007bff;
            border:none;
            color:white;
            border-radius:4px;
            cursor:pointer;
        }
        button:hover{
            background-color:#0056b3;
        }

    </style>
</head>
<body>
    <form>
        <filedset>
            <legend>Personal Information</legend>
            <div class="form-row">
                <div class="form-group">
                    <label for="fname">First Name</label>
                    <input type="text" id="fname" rqeuired />
                    <div class="error">First name is required.</div>
                </div>
                <div class="form-group">
                    <label for="lname">Last name</label>
                    <input type="text" id="lname" name="lname" />
                </div>
            </div>
        </filedset>

        <filedset>
            <legend>Contact Details</legend>
            <div class="form-row">
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="email" id="email" name="email" />
                </div>
                <div class="form-group">
                    <label for="phone">Phone Number</label>
                    <input type="tel" id="phone" name="phone" />
                </div>
            </div>
        </filedset>

        <button type="submit">Submit</button>
    </form>
    
</body>
</html>

#Q2)Responsive Hamburger Menu.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS-Only Hamburger Menu</title>
    <link rel="stylesheet" href="hamburgerMenu.css">
</head>
<body>
    <!--Hidden checkbox to toggle the menu-->
    <input type="checkbox" id="menu-toggle" />
    <label class="menu-btn" for="menu-toggle">
        <span></span>
    </label>  
    
    <!--Slide-in full screen menu-->
    <nav class="menu">
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Services</a>
        <a href="#">Contact</a>
    </nav>
</body>
</html>

Css:-
*{
    box-sizing:border-box;
}
body{
    margin:0;
    font-family:sans-serif;
}
/hide checkbox/
#menu-toggle{
    display:none;
}
/Hamburger Icon/
.menu-btn{
    position:fixed;
    top:20px;
    right:20px;
    width:30px;
    height:22px;
    cursor:pointer;
    z-index:999;
}
.menu-btn span,
.menu-btn::before,
.menu-btn::after{
      content:' ';
      position:absolute;
      height:4px;
      width:100%;
      background:#333;
      transition:all 0.4s ease;
      border-radius:2px;
}
.menu-btn span{
    top: 9px;
}
.menu-btn::before{
    top:0;
}
.menu-btn::after{
    bottom:0;
}
/transform into X when checked/
#menu-toggle:checked + .menu-btn::before{
    transform:rotate(45deg);
    top:9px;
}
#menu-toggle:checked + .menu-btn::after{
    transform:rotate(-45deg);
    bottom:9px;
}
#menu-toggle:checked + .menu-btn span{
    opacity:0;
}
/Slide-in menu styles/
.menu{
    position:fixed;
    top:0;
    right:-100%;
    width:100%;
    height:100vh;
    background: #111;
    color:white;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    transition:right 0.5s ease;
    z-index:998;
}
#menu-toggle:checked ~ .menu{
    right:0;
}
.menu a{
    color:white;
    text-decoration:none;
    font-size:2rem;
    margin:1rem 0;
    transition:color 0.3s ease;
}
.menu a:hover{
    color:#f90;
}

#Q3)Profile Settings Menu
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Custom Form Elements</title>
    <link rel="stylesheet" href="profileSetting.css">
</head>
<body>
    <div class="form-container">
        <h2>Profile Settings</h2>
        <form>
            <!--Custom Dropdown-->
            <label for="country">Select Country</label>
            <div class="Custom-select-wrapper">
                <select id="country" name="country">
                    <option value="">Choose a country</option>
                    <option value="india">India</option>
                    <option value="usa">USA</option>
                    <option value="germany">Germany</option>
                    <option value="japan">Japan</option>
                </select>
            </div>

            <!--Custom Checkbox-->
            <label>Skills</label>
            <div class="checkbox-group">
                <label class="custom-checkbox">
                    <input type="checkbox" name="skills" value="html">
                    <span>HTML</span>
                </label>
                <label class="custom-checkbox">
                    <input type="checkbox" name="skills" value="css">
                    <span>CSS</span>
                </label>
                <label class="custom-checkbox">
                    <input type="checkbox" name="skills" value="js">
                    <span>JavaScript</span>
                </label>
            </div>

            <!--Custom Radio Button-->
            <label>Gender</label>
            <div class="radio-group">
                <label class="custom-radio">
                    <input type="radio" name="gender" value="male">
                    <span>Male</span>
                </label>
                <label class="custom-radio">
                    <input type="radio" name="gender" value="female">
                    <span>Female</span>
                </label>
                <label class="custom-radio">
                    <input type="radio" name="gender" value="other">
                    <span>Other</span>
                </label>
            </div>
            <button type="submit">Submit</button>
        </form>
    </div>
</body>
</html>
Css:-
body{
    font-family:Arial, sans-serif;
    background:#f5f5f5;
    padding:40px;
}

.form-container{
    background:white;
    max-width:400px;
    margin:auto;
    padding:30px;
    border-radius:10px;
    box-shadow:0 0 15px rgba(0,0,0,0.1);
}
h2{
    text-align:center;
    margin-bottom:20px;
}
label{
    display:block;
    margin:15px 0 5px;
    font-weight:bold;
}
select{
    width:100%;
    padding:10px;
    border-radius:8px;
    border:1px solid #ccc;
    appearance: none;
    background:url('data:image/svg+xml;');
    background-size:15px;
}
.custom-checkbox,
.custom-radio{
    display:flex;
    align-items:center;
    margin:5px 0;
    position:relative;
}
.custom-checkbox input,
.custom-radio input{
    appearance:none;
    width:18px;
    height:18px;
    border:2px solid #666;
    border-radius:4px;
    margin-right:10px;
    cursor:pointer;
    position:relative;
}
.custom-radio input{
    border-radius:50%;
}
.custom-checkbox input:checked{
    background-color:#4CAF50;
    border-color:#4CAF50;
}
.custom-radio input:checked{
    background-color:#2196F3;
    border-color:#2196F3;
}
.custom-checkbox input:checked::after{
   content:"✓";
   color:white;
   font-size:14px;
   position:absolute;
   left:3px;
   top:-1px;
}
.custom-radio input:checked::after{
    content:"";
    width:8px;
    height:8px;
    background:white;
    border-radius:50%;
    position:absolute;
    left:5px;
    top:5px;
}
button{
    width:100%;
    padding:12px;
    margin-top:20px;
    background-color:#333;
    color:white;
    border:none;
    border-radius:8px;
    cursor:pointer;
}
button:hover{
    background-color:#555;
}

#Q4)Min Max attributes in HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>The Input min and max attributes</h1>

    <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ad porro et nostrum hic esse perspiciatis eum modi distinctio culpa fuga perferendis quo eaque enim aspernatur totam deleniti cum, asperiores facere?</p>

    <form action="/action_page.php">
        <label for="datemax">Enter a date before 1980-01-01:</label>
        <input type="date" id="datemax" name="datemax" max="1979-12-31"><br><br>

        <label for="datemin">Enter a date after 2000-01-01:</label>
        <input type="date" id="datemin" name="datemin" min="2000-01-02"><br><br>

        <label for="quantity">Quantity(between 1 and 5):</label>
        <input type="number" id="quantity" name="quantity" min="1" max="5"><br><br>

        <input type="submit" value="Submit">
    </form>
</body>
</html>

#Q5)Traffic Light Signal by html and css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="trafficlight.css">
</head>
<body>
    <div class="light">
        <div class="trafficlight">
            <div class="red"></div>
            <div class="yellow"></div>
            <div class="green"></div>
        </div>
    </div>
</body>
</html>
CSS:-
 .red{
    display:flex;
    background-color:red;
    height:50px;
    width:50px;
    align-items:center;
    border-radius:50%;
    margin:15px 10px;
    box-shadow:2px 1px 15px red;
}
.yellow{
    display:flex;
    background-color:rgb(255,228,26);
    height:50px;
    width:50px;
    border-radius:50%;
    margin:15px 10px;
    box-shadow:2px 1px 15px rgb(231,215,26)
}
.green{
    display:flex;
    background-color:rgb(41,201,49);
    height:50px;
    width:50px;
    border-radius:50%;
    margin: 15px 10px;
    box-shadow:2px 1px 15px rgb(62,236,36);
}
h1{
    text-align:center;
    align-items:center;
    display:flex;
}
body{
    display:flex;
    justify-content:center;
    align-items:center;
}
.trafficlight{
    background-color:black;
    border-radius:10px;
}

#Q6)Complex Table by html and css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Complex Table</title>
    <link rel="stylesheet" href="ComplexTable.css">
</head>
<body>
    <div class="table-container">
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Full Name</th>
                    <th>Email</th>
                    <th>Department</th>
                    <th>Join Date</th>
                    <th>Status</th>
                </tr>
            </thead>
            <tbody>
                <!--Repeat rows for demonstrater-->
                <tr>
                    <td>001</td>
                    <td>John Doe</td>
                    <td>john@example.com</td>
                    <td>Enginnering</td>
                    <td>2021-05-15</td>
                    <td>Active</td>
                </tr>
                <tr>
                    <td>002</td>
                    <td>Jane Smith</td>
                    <td>jane@example.com</td>
                    <td>Marketing</td>
                    <td>2020-11-21</td>
                    <td>Inactive</td>
                </tr>
            </tbody>
        </table>
    </div>
    
</body>
</html>
Css:-
body{
    font-family:Arial,sans-serif;
    margin:20px;
    background:#f4f4f4;
}
.table-container{
    overflow-x:auto;
    max-width:100%;
    background:white;
    border:1px solid #ddd;
    border-radius:6px;
}
table{
    width:100%;
    border-collapse:collapse;
    min-width:800px;
}
thead{
    background:#333;
    color:white;
    position:sticky;
    top:0;
    z-index:2;
}
thead th{
    padding:12px;
    text-align:left;
    background:#333;
}
tbody td{
    padding:12px;
    border-bottom:1px solid #ccc;
}
tbody tr:nth-child(even){
    background-color:#f9f9f9;
}
tbody tr:nth-child(odd){
    background-color:#fff;
}
@media screen and (max-width:768px){
    table{
        font-size:14px;
    }
    thead th, tbody td{
        padding:10px;
    }
}

#Q7)Real World Senario E-commerce Drop down menu
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shop Dropdown</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <nav class="menu">
        <ul>
            <li><a href="#">Home</a></li>

            <li class="has-submenu">
                <input type="checkbox" id="shop-toggle">
                <label for="shop-toggle">Shop</label>
                <ul class="submenu">
                <li><a href="#">All Products</a></li>

                <li class="has-submenu">
                <input type="checkbox" id="men-toggle">
                <label for="men-toggle">Men</label>
                <ul class="submenu">
                    <li><a href="#">Shirts</a></li>
                    <li><a href="#">Shoes</a></li>
                    <li><a href="#">Accessories</a></li>
                </ul>
                </li>
                

                <li class="has-submenu">
                    <input type="checkbox" id="women-toggle">
                    <label for="women-toggle">Women</label>
                    <ul class="submenu">
                        <li><a href="#">Dresses</a></li>
                        <li><a href="#">Handbags</a></li>
                        <li><a href="#">Jewelry</a></li>
                    </ul>
                </li>
            </li>
                </ul>
            </li>

            <li><a href="#">About Us</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </nav>
    
</body>
</html>
Css:-
body{
   font-family:'Segoe UI', sans-serif;
   background:#f8f9fa;
   padding:30px;
}

.menu ul{
    list-style:none;
    margin:0;
    padding:0;
    background:#212529;
    width:250px;
    border-radius:6px;
    overflow:hidden;
}

.menu li{
    position:relative;
}

.menu a,
.menu label{
    display:block;
    color:#f1f1f1;
    text-decoration:None;
    padding:14px 20px;
    cursor:pointer;
    transition:background 0.3s ease;
}

.menu a:hover,
.menu label:hover{
    background:#343a40;
}

input[type="checkbox"]{
    display:none;
}

.submenu{
    max-height:0;
    overflow:hidden;
    background:#343a40;
    transition: max-height 0.4s ease-in-out;
}
.has-submenu input:checked + label +.submenu{
    max-height:500px;
}

.submenu a{
    padding-left:40px;
    background:#3e444a;
}

.submenu .submenu a{
    padding-left:60px;
    background:#495057;
}

#Q8)Bulid a tabbed navigation system that switches contents on click using only css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Real Estate Property Tabs</title>
    <link rel="stylesheet" href="tabbedNavigationsystem.css">
</head>
<body>
    <div class="tabs-container">
        <!--Tab Nevigation-->
        <input type="radio" id="tab1" name="tabs" checked>
        <input type="radio" id="tab2" name="tabs">
        <input type="radio" id="tab3" name="tabs">

        <!--Tab labels-->
        <label for="tab1" class="tab-label">Property Details</label>
        <label for="tab2" class="tab-label">Photo</label>
        <label for="tab3" class="tab-label">Contact Info</label>

        <!--Tab Content-->
        <div class="tab-content" id="content1">
            <h2>Property Details</h2>
            <p><strong>Address:</Address></strong>1234 Elm Street,Springfield,IL</p>
            <p><strong>Price:</strong>$350,000</p>
            <p><strong>Size</strong>2,500 sqft</p>
            <p><strong>Bedrooms:</strong>4</p>
            <p><strong>Bathroom:</strong>3</p>
            <p><strong>Year Built:</strong>2015</p>
            <p><strong>Description:</strong>A beautiful modern home with spacious interior efficient features</p>
        </div>
        <div class="tab-content" id="content2">
            <h2>Photos</h2>
            <div class="photo-gallary">
                <img src="image.jpg" alt="Front">
                <img src="image1.jpeg" alt="Bedroom">
                <img src="image2.jpeg" alt="Hall">
                <img src="image4.jpeg" alt="Bedroom">
            </div>
        </div>
        <div class="tab-content" id="content3">
            <h2>Contact Info</h2>
            <p><strong>Agent Name:</strong>John Doe</p>
            <p><strong>Email:</strong>john.doe@example.com</p>
            <p><strong>Phone:</strong>(91+)12345667</p>
            <p><strong>Office Hours:</strong>Mon-Fri:9:00AM - 5:00PM</p>
        </div>
    </div>
    
</body>
</html>
Css:-
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}
body{
    font-family:Arial,sans-serif;
    background-color:#f4f4f4;
    padding:20px;
}
.tab-container{
    width:100%;
    max-width:900px;
    margin:0 auto;
    border:1px solid #ddd;
    border-radius:8px;
    background-color:#fff;
}
input[type="radio"]{
    display:none;
}
.tab-label{
    display:inline-block;
    padding:15px;
    text-align:center;
    background-color:#f4f4f4;
    border:1px solid #ddd;
    cursor:pointer;
    transition:background-color 0.3s ease, color blue;
}
.tab-label:hover{
    background-color:#ddd;
}
.tab-label:active{
    background-color:#bbb;
}

.tab-content{
    display:none;
    padding:20px;
    background-color:#fff;
    border-top:1px solid #ddd;
}
input#tab1:checked~.tab-content#content1,
input#tab2:checked~.tab-content#content2,
input#tab3:checked~.tab-content#content3{
    display:block;
}
input#tab1:checked~.tab-label[for="tab1"],
input#tab2:checked~.tab-label[for="tab2"],
input#tab3:checked~.tab-label[for="tab3"]{
    background-color:#007BFF;
    color:#fff;
}
.photo-gallary{
    display:grid;
    grid-template-columns:repeat(auto-fill,minmax());
    gap:10px;
    
}
.photo-gallary img{
    width:100%;
    height:auto;
    border-radius:8px;
    box-shadow:0 2px 4px rgba(0,0,0,0.1);
}

#Q9)Glassmorphic card design
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Glassmorphism Card</title>
    <link rel="stylesheet" href="GlassmorphicCardDesign.css" />
</head>
<body>
    <div class="background">
        <div class="glass-card">
            <img src="image5.jpg" width="100" height="100" class="profile-img">
            <h2>Louis Johnson</h2>
            <p>UI/UX Designer</p>
            <button>Follow</button>
        </div>
    </div>
    
</body>
</html>
Css:-
body,html{
    height:100%;
    margin:0;
    font-family:'Segoe UI',sans-serif;
}
.background{
    height:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg, #ff7eb3,rgba(20, 167, 167, 0.933))
}
.glass-card{
    width:280px;
    padding:30px;
    border-radius:20px;
    background:rgba(255,255,255,0.1);
    box-shadow:0 8px 32px rgba(0,0,0,0.25);
    backdrop-filter:blur(12px);
    -webkit-backdrop-filter:blur(12px);
    border:1px solid rgba(255,255,255,0.2);
    text-align:center;
    color:#fff;
}
.profile-img{
    width:100px;
    height:100px;
    border-radius:50%;
    border:3px solid rgba(255,255,255,0.3);
    margin-bottom:15px;
}
.glass-card h2{
    margin:10px 0 5px;
    font-size:22px;
}
.glass-card p{
    margin-bottom:20px;
    font-size:16px;
    color:#e0e0e0;
}
.glass-card button{
    padding:10px 20px;
    border:none;
    border-radius:25px;
    background-color:rgba(255,255,255,0.3);
    color:#6c2f2f;
    cursor:pointer;
    transition:background-color 0.3s;
}
.glass-card button:hover{
    background-color:rgba(255,255,255,0.5);
}

## 10. Animated Portfolio Website

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shreyas - Student Porfolio</title>
   <link rel="preconnect" href="https://fonts.google.com/specimen/Poppins">
   <link rel="preconnect" href="https://fonts.google.com/specimen/Playfair+Display">
    <style>
        * {
            margin: 0px;
            padding: 0px;
        }

        body {
            background-color: rgb(0, 0, 33);
            color: azure;
            font-family: 'Poppins', sans-serif;
        }
        nav{
            display:flex;
            justify-content:space-around;
            align-items:center;
            height:80px;
            background-color:rgb(1, 1, 51) ;
        }
        nav ul{
            display:flex;
            justify-content:center;
        }
        nav ul li{
           list-style:none;
           margin: 0 23px;
        }
        nav ul li a{
            text-decoration: none;
            color:white;
        }
        nav ul li a:hover{
          color:rgb(168, 125, 237);
          font-size:1.01rem;
        }
        main hr{
            border:0;
            background:#9c97f1;
            height:1.2px;
            margin:40px 84px;
        }

      
        .left{
            font-size:1.5rem;
        }
        .firstSection{
            display:flex;
            justify-content:space-around;
            margin:10px 0;
        }
        .firstSection > div{
            width:42%;
            
        }
        .leftsection{
            font-size: 2.7rem;
            margin:50px 0;
        }
        .leftsection .buttons{
            padding:50px 0;
        }
        .leftsection .btn{
            padding:12px;
            background:#1e2167;
            color:white;
            border:2px solid white;
            border-radius:6px;
            font-size:20px;
            cursor:pointer;
        }
        .rightsection img{
            width:80%; 
        }
        .purple{
            color:rgb(141, 75, 203);
        }
        .text-gray{
            color:gray;
        }
        #element{
            color:blueviolet;
        }
        .secondSection{
            max-width:80vw;
            margin:auto;
            height:80vh;
        }
        .secondSection h1{
            font-size:1.9rem;
        }
        .secondSection .box {
            background:white;
            width:80vw;
            height:2px;
            margin:56px 0;
            display:flex;
        }
        .secondSection .vertical{
            height:93px;
            width:1px;
            background-color:white;
            margin:0 100px; 
        }
        .image-top{
            width:23px;
            position: relative;
            top:-32px;
            left:-9px;
        }
        .vertical-title{
            position: relative;
            top:75px;
            width:150px;
            font-size: 14px;
        }
        .vertical-desc{
            position: relative;
            top:86px;
            color: grey;
            width: 150px;
            font-size: 9px;

        }
        footer{
            background-color:#0e0e1a;
          

        }
        .footer{
            display:flex;
            padding:23px 122px;
            justify-content:space-evenly ;
        }
        .footer ul{
            list-style:none;
        }
        .footer > div{
            width: 100px;
        }
        
        footer .footer-rights{
            text-align:center;
            color:gray;
            padding:12px 0;
        }
    </style>
</head>

<body>
    <header>
        <nav>
            <div class="left">Shreyas Porfolio</div>
            <div class="right">
                <ul>
                    <li><a href="/">Home</a></li>
                    <li><a href="/">About</a></li>
                    <li><a href="/">Certificates</a></li>
                    <li><a href="/">Projects</a></li>
                    <li><a href="/">Contact Me</a></li>

                </ul>
            </div>
        </nav>
    </header>
    <main>
        <section class="firstSection">
            <div class="leftsection">
                Hi, My name is <span class="purple">Shreyas</span>
                <div>and I am a Student of Sanjivani University </div>
                <span id="element"></span>
                <div class="buttons">
                    <button class="btn">Download Resume</button>
                    <button class="btn">Visit Github</button>
                </div>
            </div>
            <div class="rightsection">
                <img src="https://png.pngtree.com/png-vector/20240312/ourmid/pngtree-smart-college-student-using-computer-at-home-he-is-studying-and-png-image_11716756.png">
               
            </div>
        </section>
        <hr>
        <section class="secondSection">
            <span class="text-gray">What I have done so far</span>
            <h1>Skills</h1>
            <div class="box">
            <div class="vertical">
                <img class="image-top" src="htmlcss3.png" alt="">
                <div class="vertical-title">
                    HTML CSS Developer
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div>
            <div class="vertical">
                <img class="image-top" src="python.png" alt="">
                <div class="vertical-title">
                  Basics Python Coding
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div> <div class="vertical">
                <img class="image-top" src="javascript.png" alt="">
                <div class="vertical-title">
                   Basics Javascript Coding
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div> 
            <div class="vertical">
                <img class="image-top" src="C++.png" alt="">
                <div class="vertical-title">
                    Basics C++ Coding(DSA)
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div>
            <div class="vertical">
                <img class="image-top" src="developer1.png" alt="">
                <div class="vertical-title">
                   UI/UX Designer(Figma)
                </div>
                <div class="vertical-desc">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores, voluptatum? Expedita, delectus dolorem fugiat eaque in obcaecati animi vitae voluptates doloremque quam corrupti nobis modi consequatur dolore saepe cumque ipsum!
                </div>
            </div>
         
        </section>
    </main>
    <footer>
        <div class="footer">
            <div class="footer-first">
                Shreyas Kulat Portfolio
            </div>
            <div class="footer-second">
            <ul>
                <li>Home</li>
                <li>About</li>
                <li>Project</li>
                <li>Contact</li>
            </ul>
            </div>
            <div class="footer-third">
            <ul>
                <li>Home</li>
                <li>About</li>
                <li>Project</li>
                <li>Contact</li>
            </ul>
            </div>
            <div class="footer-fourth">
            <ul>
                <li>Home</li>
                <li>About</li>
                <li>Project</li>
                <li>Contact</li>
            </ul>
            </div>
        </div>
            <div class="footer-rights">
                Copyright &#169;.shreyasportfolio.com | All rights reserved
            </div>
        
    </footer>
    <script src="https://unpkg.com/typed.js@2.1.0/dist/typed.umd.js"></script>
    <script>
        var typed = new Typed('#element', {
          strings: ['Studying in CSE', 'Specilization in AIML'],
          typeSpeed: 50,
        });
      </script>
</body>

</html>,


# HTML, CSS & JS Comprehensive Guide

## 1. <picture> Element vs. <img> with srcset

### Theory
The <picture> Element:
- Allows specifying multiple image sources based on media conditions
- Uses <source> elements for different media queries and image types
- Useful for art direction - providing different images or croppings for different viewport sizes

The <img> with srcset:
- Provides responsive images by offering image candidates with descriptors (width or pixel density)
- Browser picks the best-fit image based on inherent image conditions
- Cannot change the "art" or composition of the image

When to Use Each:
- Use <picture> when you need to change the image completely (different cropping or composition) based on viewport size
- Use <img> with srcset when you only need multiple resolutions of the same image

### Code Examples

Using <picture> for art direction:
html
<picture>
  <!-- For wide screens -->
  <source media="(min-width: 800px)" srcset="images/landscape-large.jpg">
  <!-- For smaller screens -->
  <source media="(max-width: 799px)" srcset="images/landscape-small.jpg">
  <!-- Fallback image -->
  <img src="images/landscape-small.jpg" alt="A beautiful landscape">
</picture>


Using <img> with srcset for resolution switching:
html
<img src="images/photo-1x.jpg"
     srcset="images/photo-1x.jpg 1x, images/photo-2x.jpg 2x"
     alt="A descriptive photo">


## 2. defer vs. async Attributes in <script>

### Theory
defer:
- Downloads script while continuing to parse HTML
- Executes script only after parsing is complete
- Scripts marked with defer preserve their execution order
- Ideal for scripts that depend on the full DOM

async:
- Downloads script while parsing HTML
- Executes script as soon as it's available, regardless of HTML parsing progress
- Order of execution is not guaranteed with multiple async scripts
- Best for independent scripts (tracking, analytics) that don't rely on the DOM

### Code Examples
html
<!-- Deferred scripts execute in order after HTML parsing -->
<script src="script1.js" defer></script>
<script src="script2.js" defer></script>

<!-- Async script loads and executes as soon as ready -->
<script src="analytics.js" async></script>


## 3. Web Components: Shadow DOM, Custom Elements, and HTML Templates

### Theory
Web Components are a set of standards for creating reusable custom elements with encapsulated functionality and styling:

Custom Elements:
- Define new HTML tags with custom behavior

Shadow DOM:
- Provides encapsulated DOM and style scoping
- Prevents component styles from leaking out or being affected by global styles

HTML Templates:
- Define markup that isn't rendered until explicitly instantiated
- Ideal for repeating structures and reusable content

### Code Example
html
<!-- Define a template -->
<template id="my-component-template">
  <style>
    .container {
      border: 2px solid #333;
      padding: 1rem;
      background-color: #f9f9f9;
    }
  </style>
  <div class="container">
    <h2>Custom Component</h2>
    <p>This is a reusable web component.</p>
  </div>
</template>

<script>
  // Define a custom element class
  class MyComponent extends HTMLElement {
    constructor() {
      super();
      // Attach a shadow DOM tree to this element.
      const shadow = this.attachShadow({mode: 'open'});
      // Find the template and clone its content.
      const template = document.getElementById('my-component-template');
      const templateContent = template.content.cloneNode(true);
      // Append the cloned template to the shadow root.
      shadow.appendChild(templateContent);
    }
  }
  // Register the custom element.
  customElements.define('my-component', MyComponent);
</script>

<!-- Use the custom element -->
<my-component></my-component>


## 4. <datalist> vs. <select> Dropdown

### Theory
*<datalist>:*
- Works as an autocomplete feature for <input> elements
- Provides suggestions while allowing any value to be entered
- More flexible but with less control

*<select> Dropdown:*
- Displays a closed list of predefined options
- User must choose from the provided options
- More structured and controlled

*Limitations of <datalist>:*
- Limited styling options (browser-dependent appearance)
- No guarantee of enforcing selection from the list
- Inconsistent support for features like grouping

### Code Examples

Using <datalist>:
html
<input list="browsers" name="browser">
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
  <option value="Edge">
</datalist>


Using <select>:
html
<select name="browser">
  <option value="Chrome">Chrome</option>
  <option value="Firefox">Firefox</option>
  <option value="Safari">Safari</option>
  <option value="Edge">Edge</option>
</select>


## 5. Resource Hints: rel="preload", rel="preconnect", and rel="prefetch"

### Theory
preload:
- Instructs browser to load resources as soon as possible
- Used for critical assets like fonts, scripts, or stylesheets
- Prioritizes resources regardless of where they appear in the document

preconnect:
- Establishes early connections (DNS, TCP, TLS) to specified domains
- Reduces latency when resources are later fetched from those domains

prefetch:
- Provides hints about resources that might be needed in the future
- Browser fetches these resources during idle time
- Useful for resources needed for subsequent navigation

### Code Examples
html
<!-- Preload critical stylesheet -->
<link rel="preload" href="styles/critical.css" as="style">
<link rel="stylesheet" href="styles/critical.css">

<!-- Preconnect to a third-party domain -->
<link rel="preconnect" href="https://api.example.com">

<!-- Prefetch resources for next page -->
<link rel="prefetch" href="next-page-content.html">


## 6. The contenteditable Attribute and Creating a Rich-Text Editor

### Theory
contenteditable:
- Makes an element editable in the browser
- Users can modify content directly on the page

Rich-text editor creation:
- Combine contenteditable with JavaScript toolbars for formatting
- Use document.execCommand() or modern libraries for editing functions

### Code Example
html
<!-- Editable div for rich text -->
<div id="editor" contenteditable="true" style="border: 1px solid #ccc; padding: 10px;">
  <p>Edit this content...</p>
</div>

<!-- Simple toolbar using buttons -->
<button onclick="document.execCommand('bold')">Bold</button>
<button onclick="document.execCommand('italic')">Italic</button>
<button onclick="document.execCommand('underline')">Underline</button>


## 7. <details> and <summary> Elements

### Theory
Usage:
- <details> creates an interactive widget users can open and close
- <summary> provides a visible heading for the details section

Accessibility Considerations:
- Ensure <summary> text is descriptive
- Keyboard accessibility is built-in (Enter/Space to toggle)
- Screen readers announce when a section is expandable

### Code Example
html
<details>
  <summary>More Information</summary>
  <p>Here is the additional content that can be toggled by the user.</p>
</details>


## 8. ARIA Attributes: aria-label, aria-labelledby, and aria-describedby

### Theory
aria-label:
- Provides an invisible label where a visible text label isn't present
- Useful for icons or complex controls

aria-labelledby:
- References the ID of another element that provides a label
- Used when the label is visible elsewhere in the DOM

aria-describedby:
- Identifies elements that describe the object
- Helpful for extra context, instructions, or error messages

Usage Guidelines:
- Use aria-label for simple, standalone labels
- Use aria-labelledby when you already have an associated element acting as a label
- Use aria-describedby for additional explanatory text

### Code Example
html
<!-- Using aria-label -->
<button aria-label="Close" onclick="closeModal()">X</button>

<!-- Using aria-labelledby -->
<label id="usernameLabel" for="username">Username:</label>
<input id="username" type="text" aria-labelledby="usernameLabel">

<!-- Using aria-describedby -->
<input id="email" type="email" aria-describedby="emailHint">
<small id="emailHint">We will not share your email.</small>


## 9. The sandbox Attribute in <iframe>

### Theory
Purpose:
- Adds security restrictions on content rendered inside an <iframe>
- Disables features like form submission, script execution, and same-origin access unless explicitly allowed

Secure Embedding of Third-Party Content:
- Apply the sandbox attribute with appropriate flags to limit what third-party content can do
- Reduces risk of malicious behavior

### Code Example
html
<iframe src="https://trusted-thirdparty.com"
        sandbox="allow-scripts allow-same-origin"
        width="600"
        height="400"
        title="Embedded Third Party Content">
</iframe>


