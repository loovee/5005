<head>

  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <title>SITE_NAME</title>

  <link rel="apple-touch-icon" sizes="76x76" href="SITE_LOGO">
  <link rel="icon" type="image/png" href="SITE_LOGO">

  <!-- Bootstrap core CSS -->
  <link rel="stylesheet" href="./assets/vendor/bootstrap/css/bootstrap.min.css">
     <link rel="stylesheet" href="/assets/css/main.css"> 
  <style>
    <br />
<b>Warning</b>:  file_get_contents(ABSPATH/assets/css/main.css): failed to open stream: No such file or directory in <b>/www/wwwroot/haivip/index.php</b> on line <b>17</b><br />
  </style>
<style>

.loader{
  position: fixed;
  left: 0px;
  top: 0px;
  width: 100%;
  height: 100%;
  z-index: 9999;
  background: url('https://i.pinimg.com/originals/8f/2d/2b/8f2d2b5bf954350643ff3642d9c315df.gif') 
              50% 50% no-repeat rgb(249,249,249);
}    
</style>
<meta property="og:image" content="" /><meta property="og:title" content="" /><img class="loader" />
  <!-- Custom styles for this template -->

  <script>
    var SITE_ADDR = 'https://placehold.xyz';
    
    // ready the sites javascript for use after the page has loaded
    window.onload = function() {
      
      // select the url text box on page load
      $("#url").focus();

      // process the form submission using javascript
      $("#form").submit(function(event) {
        $("#copy").hide();

        // get the url to be shortened
        var url = $("#url").val();
        var og_title = $("#og_title").val();
        var og_tag = $("#og_tag").val();
        if ($.trim(url) != '') {
          // submit all of the required data via post to the processing script
          $.post("./process.php", {
            url: url,
            og_title,
            og_tag: og_tag
          }, function(data) {
            // process the returned data from the post
            $("#result_url").show();
             $("#result_url").val(data).focus();
          });
        } else
          $("#message").text("enter a url to shorten");

        // select the text box after form submission
        $("#url").focus();
        // prevent the form from reloading the page
        return false;
      });


    };
  </script>
  
</head>

<body>

  <article>
    <div class="">
      <h1>
        <a href="https://placehold.xyz"><img class="logo" alt="fii.sh url shortener" src="./assets/img/logo.png" width="100" height="100"></img>
         </a>
      </h1>
    </div>

    <div class="clearfix"></div>

    <div class="row my-4">
      <div class="offset-sm-1 col-sm-10 col-xs-12 card shadow-sm p-5 bg-orange-light text-center">
        <form action="" method="post" id="form" onSubmit="return false;">
          <div class="input-group mb-3">

            <input type="text" id="url" class="form-control" value="" placeholder="enter a url" tabindex="1" active />
            <div class="input-group-prepend" id="copy" style="display:none;">
              <span class="input-group-text bg-orange-dark">copy</span>
            </div>
          </div>
             <div class="input-group mb-3">
                 <input type="text" id="og_title" class="form-control" value="" placeholder="enter title" tabindex="1" active /> 
             </div>            
             <div class="input-group mb-3">
                 <input type="text" id="og_tag" class="form-control" value="" placeholder="enter thumbnai image url" tabindex="1" active /> 
             </div>          
          <br />
          <button type="submit" name="short" class="form-control btn w-75 bg-orange-dark" tabindex="2">make short</button>
        </form>
         <div class="mt-3 mb-3">
             <input type="text"  style="display: none;" id="result_url" class="form-control" value="" placeholder="enter title" tabindex="1" active /> 
         </div>          
    </div>

  </article>


  <script src="./assets/vendor/jquery/jquery-3.5.1.min.js"></script>
</body>
</html>
