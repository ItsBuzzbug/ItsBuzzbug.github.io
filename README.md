# Elements the Typology
Welcome to "Elements the Typology" wiki!
"Elements" are based on assymetrical tetrachomies from analytical psychology, which defines person's <b>Rhetorical Appeal</b> and <b>Interaction style</b>

<h1> Elements </h1>
Person's main Element shows how person usually interact with others:
<ul> <li><b> Fire </b> — order and control their subordinates to get results faster. They collect resources and direct them to the cause. </li> <li> <b>Water</b> —  support their subordinates and direct their work from behind the scenes. They praise their employees, adapt to changes, and resolve technical issues. </li> <li> <b>Air</b> — discuss different options, brainstorm, and discover new opportunities for their teams. They involve others in their work and help them come up with new ideas. </li> <li> <b>Earth</b> —  develop an action plan, plan everything down to the smallest detail, and monitor the work of others. They direct their team's efforts to achieve their goals. </li>  </ul>
<h1> Appeal </h1>
Person's Appeal describes person appeal:
<ul> <li><b> Thinking </b> </li> <li> <b>Loving</b> </li> <li> <b>Immutable</b> </li> <li> <b>Fatal</b> </li>  </ul>

<u>based on correspondence to the Aristotelian rhetorical appeals</u>

<h1>Sub-types</h1>

Click on the sub-type name to read a page about it (CURRENTLY NOT WORKING)
<table><tbody>
  <tr>
    <td></td>
    <td>Fire (F)</td>
    <td>Water (W)</td>
    <td>Air (A)</td>
    <td>Earth (E)</td>
  </tr>
  <tr>
    <td>Thinking (T)</td>
    <td>Torch (TF) </td>
    <td>Ice (TW)</td>
    <td>Wind (TA) </td>
    <td>  Tree (TE)</td>
  </tr>
  <tr>
    <td>Loving (L)</td>
    <td>Flame (LF)</td>
    <td>Spring (LW)</td>
    <td>Calm (LA)</td>
    <td>Flower (LE)</td>
  </tr>
  <tr>
    <td>Immutable (I)</td>
    <td>Hearth (IF)</td>
    <td>Lake (IW)</td>
    <td>Draft (IA)</td>
    <td>Rock (IE)</td>
  </tr>
  <tr>
    <td>Fatal (F)</td>
    <td>Lightning (FF)</td>
    <td>Waterfall (FW)</td>
    <td>Storm (FA)</td>
    <td>Metal (FE)</td>
  </tr>
</tbody>
</table>

<div class="container">    <label for="newComment" name="newComment">Add your comment below-</label>    <textarea id="newComment"></textarea>    <button id="addComments">Add Comment</button>    <div id="allComments"></div></div>


const commentContainer = document.getElementById('allComments');document.getElementById('addComments').addEventListener('click', function (ev) {   addComment(ev);});function addComment(ev) {    let commentText, wrapDiv;    const textBox = document.createElement('div');    const replyButton = document.createElement('button');    replyButton.className = 'reply';    replyButton.innerHTML = 'Reply';    const likeButton = document.createElement('button');    likeButton.innerHTML = 'Like';    likeButton.className = 'likeComment';    const deleteButton = document.createElement('button');    deleteButton.innerHTML = 'Delete';    deleteButton.className = 'deleteComment';    const wrapDiv = document.createElement('div');    wrapDiv.className = 'wrapper';    wrapDiv.style.marginLeft = 0;    commentText = document.getElementById('newComment').value;    document.getElementById('newComment').value = '';    textBox.innerHTML = commentText;    wrapDiv.append(textBox, replyButton, likeButton, deleteButton);    commentContainer.appendChild(wrapDiv);    }


function hasClass(elem, className) {    return elem.className.split(' ').indexOf(className) > -1;}document.getElementById('allComments').addEventListener('click', function (e) {    if (hasClass(e.target, 'reply')) {        const parentDiv = e.target.parentElement;        const wrapDiv = document.createElement('div');        wrapDiv.style.marginLeft = (Number.parseInt(parentDiv.style.marginLeft) + 15).toString() + 'px';        wrapDiv.className = 'wrapper';        const textArea = document.createElement('textarea');        textArea.style.marginRight = '20px';        const addButton = document.createElement('button');        addButton.className = 'addReply';        addButton.innerHTML = 'Add';        const cancelButton = document.createElement('button');        cancelButton.innerHTML = 'Cancel';        cancelButton.className='cancelReply';        wrapDiv.append(textArea, addButton, cancelButton);        parentDiv.appendChild(wrapDiv);    } else if(hasClass(e.target, 'addReply')) {        addComment(e);    } else if(hasClass(e.target, 'likeComment')) {         const likeBtnValue = e.target.innerHTML;         e.target.innerHTML = likeBtnValue !== 'Like' ? Number.parseInt(likeBtnValue) + 1 : 1;    } else if(hasClass(e.target, 'cancelReply')) {        e.target.parentElement.innerHTML = '';    } else if(hasClass(e.target, 'deleteComment')) {        e.target.parentElement.remove();    }});


function addComment(ev) {    let commentText, wrapDiv;    const textBox = document.createElement('div');    const replyButton = document.createElement('button');    replyButton.className = 'reply';    replyButton.innerHTML = 'Reply';    const likeButton = document.createElement('button');    likeButton.innerHTML = 'Like';    likeButton.className = 'likeComment';    const deleteButton = document.createElement('button');    deleteButton.innerHTML = 'Delete';    deleteButton.className = 'deleteComment';    if(hasClass(ev.target.parentElement, 'container')) {        const wrapDiv = document.createElement('div');        wrapDiv.className = 'wrapper';        wrapDiv.style.marginLeft = 0;        commentText = document.getElementById('comment').value;        document.getElementById('comment').value = '';        textBox.innerHTML = commentText;        wrapDiv.append(textBox, replyButton, likeButton, deleteButton);        commentContainer.appendChild(wrapDiv);    } else {        wrapDiv = ev.target.parentElement;        commentText = ev.target.parentElement.firstElementChild.value;        textBox.innerHTML = commentText;        wrapDiv.innerHTML = '';        wrapDiv.append(textBox, replyButton, likeButton, deleteButton);    }  }


function setOnLocalStorage () {    localStorage.setItem('template', document.getElementById('allComments').innerHTML);}
Create a Comment Box in HTML and CSS
In HTML, create a section with an id "app" and place a textarea (for comment input) and p element for comment output. <section id="app"> <div class="container"> <div class="row"> <div class="col-6"> <div …

<section id="app">
    <div class="container">
      <div class="row">
        <div class="col-6">
          <div class="comment">
        <p v-for="items in item" v-text="items"></p>
          </div><!--End Comment-->
          </div><!--End col -->
          </div><!-- End row -->
      <div class="row">
        <div class="col-6">
      <textarea type="text" class="input" placeholder="Write a comment" v-model="newItem" @keyup.enter="addItem()"></textarea>
          <button v-on:click="addItem()" class='primaryContained float-right' type="submit">Add Comment</button>
        </div><!-- End col -->
      </div><!--End Row -->
    </div><!--End Container -->
  </section><!-- end App -->



.container {
    max-width: 640px;
    margin: 30px auto;
    background: #fff;
    border-radius: 8px;
    padding: 20px;
}



.comment {
    display: block;
    transition: all 1s;
}
.commentClicked {
    min-height: 0px;
    border: 1px solid #eee;
    border-radius: 5px;
    padding: 5px 10px
}



.container textarea {
    width: 100%;
    border: none;
    background: #E8E8E8;
    padding: 5px 10px;
    height: 50%;
    border-radius: 5px 5px 0px 0px;
    border-bottom: 2px solid #016BA8;
    transition: all 0.5s;
    margin-top: 15px;
}



button.primaryContained {
    background: #016ba8;
    color: #fff;
    padding: 10px 10px;
    border: none;
    margin-top: 0px;
    cursor: pointer;
    text-transform: uppercase;
    letter-spacing: 4px;
    box-shadow: 0px 2px 6px 0px rgba(0, 0, 0, 0.25);
    transition: 1s all;
    font-size: 10px;
    border-radius: 5px;
}



button.primaryContained:hover {
    background: #9201A8;
}



<!-- Vue JS -->
<script src='https://cdnjs.cloudflare.com/ajax/libs/vue/2.5.17/vue.min.js'></script>
<!-- jQuery -->
<script src='https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js'></script>



$(document).ready(function(){ 

    $(".primaryContained").on('click', function(){
    $(".comment").addClass("commentClicked");
  });//end click
  $("textarea").on('keyup.enter', function(){
    $(".comment").addClass("commentClicked");
  });//end keyup
  });//End Function

new Vue({
    el: "#app",
    data:{
       title: 'Add a comment',
      newItem: '',
      item: [],
    },
    methods:{
      addItem  (){
      this.item.push(this.newItem);
        this.newItem = "";
      }
  }

  });



CREATE TABLE comments(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NULL UNIQUE,
    email VARCHAR(255) NULL UNIQUE,
    comment TEXT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);



<?php
//Define variables for requested input fields
$username = $email = $comment = "";

if ($_SERVER["REQUEST_METHOD"] == "POST") {

        $username = test_input($_POST["complainant-name"]);
        $email = test_input($_POST["bill-account"]);
        $comment = test_input($_POST["amount-payable"]);

        //connect to databse
        define('DB_SERVER', 'localhost');
        define('DB_USERNAME', 'root');
        define('DB_PASSWORD', '');
        define('DB_NAME', 'yourdbname');

        /* Attempt to connect to MySQL database */
        $link = mysqli_connect(DB_SERVER, DB_USERNAME, DB_PASSWORD, DB_NAME);

        // Check connection
        if($link === false){
            die("ERROR: Could not connect. " . mysqli_connect_error());
        }

        $sql = "INSERT INTO comments(
        username, 
        email, 
        comment
        )  

        VALUES (
        '".$username."', 
        '".$email."', 
        '".$comment."
        )";

        if ($link->query($sql) === TRUE) {

            echo "Your comment has been submitted!";

        } 
        else {
            echo "Error: " . $sql . "<br>" . $link->error;
        }

        $link->close();

}
else {
    //nothing
}

function test_input($data) {
    $data = trim($data);
    $data = stripslashes($data);
    $data = htmlspecialchars($data);
    return $data;
}

?>



<form action="post-comment.php"></form>



.comment{
    height: 300px;
    overflow-y: scroll;
}



<div class="username"> <b> Username </b></div>

