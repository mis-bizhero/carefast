# SDA Form

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SDA Provider Group Enquiry Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            padding: 20px;
        }
        form {
            width: 50%;
            margin: 0 auto;
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.1);
        }
        h2 {
            font-weight: bold;
            text-align: center;
            margin-bottom: 20px;
            background-color: #4169E1; /* Change to your desired background color */
            color: white; /* Add text color to improve readability */
            padding: 10px; /* Add padding for better appearance */
        }
        form {
            width: 50%;
            margin: 0 auto;
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.1);
        }
        label {
            font-weight: bold;
            display: block;
            margin-bottom: 5px;
            background-color: #f5f5f5; /* Change background color here */
            color: black; /* Change text color to white */
            padding: 5px 10px; /* Add padding for better appearance */
            border-radius: 5px; /* Add border radius for rounded corners */
        }
        input[type="text"],
        input[type="email"],
        textarea {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
        }
        input[type="checkbox"] {
            display: inline-block;
            vertical-align: middle;
            margin-right: 5px;
        }
        .checkbox-label {
            display: inline-block;
            vertical-align: middle;
            margin-right: 20px;
        }
        textarea {
            height: 100px;
        }
        input[type="submit"] {
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
        }
        input[type="submit"]:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

<h2>SDA Provider Group Enquiry Form</h2>

<form action="https://formspree.io/f/your-form-id" method="post">
    <label for="orgName">Name of Organization/Group:</label>
    <input type="text" id="orgName" name="orgName" required><br>
    
<label for="contactPerson">Contact Person:</label>
    <input type="text" id="contactPerson" name="contactPerson" required><br>
    
   <label for="position">Position/Title:</label>
    <input type="text" id="position" name="position" required><br>
   
   <label for="email">Email Address:</label>
    <input type="email" id="email" name="email" required><br>
    
   <label for="phone">Phone Number:</label>
    <input type="text" id="phone" name="phone" required><br>
    
   <label for="address">Address:</label>
    <textarea id="address" name="address" required></textarea><br>
    
   <label>Type of Enquiry:</label>
  
   <input type="checkbox" id="general" name="enquiryType" value="General Inquiry">
    <label class="checkbox-label" for="general">General Inquiry</label><br>
    
   <input type="checkbox" id="partnership" name="enquiryType" value="Partnership Opportunity">
    <label class="checkbox-label" for="partnership">Partnership Opportunity</label><br>
    
   <input type="checkbox" id="collaboration" name="enquiryType" value="Project Collaboration">
    <label class="checkbox-label" for="collaboration">Project Collaboration</label><br>
    
   <input type="checkbox" id="other" name="enquiryType" value="Other">
    <label class="checkbox-label" for="other">Other</label><br><br>
    
   <label for="description">Description of Enquiry:</label><br>
    <textarea id="description" name="description" required></textarea><br>
    
   <label for="services">Service Offerings:</label><br>
    <textarea id="services" name="services"></textarea><br>
    
   <label for="experience">Experience and Expertise:</label><br>
    <textarea id="experience" name="experience"></textarea><br>
    
   <label for="collaborationInterests">Collaboration Interests:</label><br>
    <textarea id="collaborationInterests" name="collaborationInterests"></textarea><br>
    
   <label for="comments">Additional Comments or Questions:</label><br>
    <textarea id="comments" name="comments"></textarea><br>
    
   <input type="checkbox" id="declaration" name="declaration" required>
    <label for="declaration">I agree to the terms and conditions.</label><br>
    
   <input type="submit" value="Submit Enquiry">
</form>

</body>
</html>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
   $orgName = $_POST['orgName'];
   $contactPerson = $_POST['contactPerson'];
   $position = $_POST['position'];
  $email = $_POST['email'];
   $phone = $_POST['phone'];
   $address = $_POST['address'];
   $enquiryType = $_POST['enquiryType'];
   $description = $_POST['description'];
   $services = $_POST['services'];
   $experience = $_POST['experience'];
   $collaborationInterests = $_POST['collaborationInterests'];
   $comments = $_POST['comments'];

    // Compose email message
   $to = 'mis@bizhero.com.au';
   $subject = 'SDA Provider Group Enquiry';
   $message = "Organization/Group: $orgName\n\nContact Person: $contactPerson\n\nPosition/Title: $position\n\nEmail: $email\n\nPhone: $phone\n\nAddress: $address\n\nType of Enquiry: $enquiryType\n\nDescription of Enquiry: $description\n\nService Offerings: $services\n\nExperience and Expertise: $experience\n\nCollaboration Interests: $collaborationInterests\n\nAdditional Comments or Questions: $comments";

   // Send email
   $headers = 'From: ' . $email . "\r\n" .
        'Reply-To: ' . $email . "\r\n" .
        'X-Mailer: PHP/' . phpversion();

    mail($to, $subject, $message, $headers);

    // Redirect back to the form page
    header("Location: enquiry_form.html");
    exit;
}
?>
