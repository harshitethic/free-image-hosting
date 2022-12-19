<?php

// Set the maximum file size for uploaded images
$max_file_size = 500000; // 500KB

// Set the allowed file types
$allowed_types = array("image/jpeg", "image/png", "image/gif");

// Check if the form has been submitted
if (isset($_POST['submit'])) {
  // Check if a file has been selected for upload
  if (!empty($_FILES['image']['name'])) {
    // Check if the file size is within the allowed limit
    if ($_FILES['image']['size'] <= $max_file_size) {
      // Check if the file type is in the allowed list
      if (in_array($_FILES['image']['type'], $allowed_types)) {
        // Generate a unique file name
        $file_name = uniqid() . "." . pathinfo($_FILES['image']['name'], PATHINFO_EXTENSION);
        // Set the destination for the uploaded file
        $upload_dir = "uploads/";
        $upload_file = $upload_dir . $file_name;
        // Attempt to move the uploaded file
        if (move_uploaded_file($_FILES['image']['tmp_name'], $upload_file)) {
          // Display a message if the file was successfully uploaded
          echo "Your image was uploaded successfully!";
        } else {
          // Display an error message if the file was not uploaded
          echo "There was an error uploading your image.";
        }
      } else {
        // Display an error message if the file type is not allowed
        echo "Sorry, only JPEG, PNG, and GIF files are allowed.";
      }
    } else {
      // Display an error message if the file size is too large
      echo "Sorry, the file size must be less than 500KB.";
    }
  } else {
    // Display an error message if no file was selected for upload
    echo "You must select an image to upload.";
  }
}

?>

<!-- Display a form for uploading images -->
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="post" enctype="multipart/form-data">
  <input type="file" name="image">
  <input type="submit" name="submit" value="Upload">
</form>
