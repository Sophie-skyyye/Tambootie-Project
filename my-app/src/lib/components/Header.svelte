<section class="header">
    <nav>
      <a href="home"><img src="Images/logo3.png"></a>  
      <div class="links">
        <ul>
            <li><a href="home">HOME</a></li>
            <li><a href="about">ABOUT</a></li>
            <li><a href="courses">COURSES</a></li>
            <li><a href="blog">BLOG</a></li>
            <li><a href="contact">CONTACT</a></li>
        </ul>
      </div>
    </nav>
    <div class="textbox">
        <h1>Tambotie Wildlife Rehab</h1>
        <p>Providing shade, food and a home to all animals</p>
         <a href="https://maps.app.goo.gl/TAKn3MYW2UGffJka8" class="Vist-button">Visit us to know more</a> 
    </div>
</section>

<style>
  .header{
    min-height: 100vh;
    width: 100%;
    background-image: linear-gradient(rgba(4,9,30,0.7),rgba(4,9,30,0.7)),url(/Images/Banner.jpg);
    background-position: center;
    background-size: cover;
    position: relative;
}

nav{
    display: flex;
    padding: 2% 6%;
    justify-content: space-between;
    align-items: center;
}

nav img{
    border-radius: 50%;
    width: 140px;
    height: 140px;
    object-fit: cover;    
}

.links{
    flex: 1;
    text-align: right;
}

.links ul li{
    list-style: none;
    display: inline-block;
    padding: 8px 12px;
    position: relative;
}

.links ul li a{
    color: #fff;
    text-decoration: none;
    font-size: 13px;
}

.links ul li::after{
    content: '';
    width: 0%;
    height: 2px;
    background: #fae18f;
    display: block;
    margin: auto;
    transition: 0.5s;
}

.links ul li:hover::after {
    width: 100%;
}

.textbox{
    width: 90%;
    color: #fff;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);   
    text-align: center;
}
.textbox h1{
    font-size: 62px; 
}

.textbox p{
    margin: 10px 0 40px;
    font-size: 14px;
    color: #fff;
}

.Vist-button{
    display: inline-block;
    text-decoration: none;
    color: #fff;
    border: 1px solid #fff;
    padding: 12px 34px;
    font-size: 13px;
    background: transparent;
    position: relative;
    cursor: pointer;
}

.Vist-button:hover{
    border: 1px solid #fae18f;
    background: #fae18f;
    transition: 1s;
}

@media (max-width: 800px) {
    .header{
        min-height: 70vh;
    }

    .textbox h1 {
        font-size: 20px; 
    }

    .textbox p {
        font-size: 10px; 
    }

    .links {
        padding: 1% 2%; 
    }

    .links ul li {
        padding: 1px 1px; 
    }

    .Contact-button,
    .Vist-button {
        padding: 10px 20px; 
        font-size: 12px; 
    }

} 
</style>