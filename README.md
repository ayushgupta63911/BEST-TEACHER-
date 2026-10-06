<?php

$host = "localhost";
$dbname = "tuition_portal";
$username = "root";
$password = "";

$conn = new mysqli($host, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Database connection failed.");
}

$conn->set_charset("utf8mb4");

session_start();
?>
CREATE DATABASE tuition_portal;

USE tuition_portal;

CREATE TABLE student_requirements (
    id INT AUTO_INCREMENT PRIMARY KEY,
    parent_name VARCHAR(100) NOT NULL,
    student_name VARCHAR(100) NOT NULL,
    mobile VARCHAR(20) NOT NULL,
    student_class VARCHAR(50) NOT NULL,
    subject VARCHAR(100) NOT NULL,
    board VARCHAR(100),
    area VARCHAR(150),
    preferred_time VARCHAR(100),
    mode VARCHAR(30),
    special_requirement TEXT,
    status VARCHAR(30) DEFAULT 'Pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE teachers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    teacher_name VARCHAR(100) NOT NULL,
    mobile VARCHAR(20) NOT NULL,
    email VARCHAR(150),
    qualification VARCHAR(200),
    subjects VARCHAR(300),
    classes VARCHAR(200),
    board VARCHAR(100),
    experience VARCHAR(100),
    teaching_area VARCHAR(150),
    additional_information TEXT,
    class10_marksheet VARCHAR(255),
    class12_marksheet VARCHAR(255),
    aadhaar_document VARCHAR(255),
    status VARCHAR(30) DEFAULT 'Pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE admin (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL
);

INSERT INTO admin (username, password)
VALUES ('admin', '$2y$10$92IXUNpkjO0rOQ5byMi.Ye4oKoEa3Ro9llC6v7lYwR7rTj9b1u3i');
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EduMatch - Teacher & Student</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>

<header>
    <div class="logo">Edu<span>Match</span></div>

    <nav>
        <a href="#home">Home</a>
        <a href="#how">How It Works</a>
        <a href="#about">About</a>
    </nav>
</header>

<section class="hero" id="home">

    <div class="hero-content">

        <div class="badge">Personalized Learning Platform</div>

        <h1>
            Find the Right
            <span>Teacher or Student</span>
        </h1>

        <p>
            Connect with the right learning opportunity.
            Submit your requirement and our team will help you find the right match.
        </p>

        <a href="#requirement" class="main-btn">
            Get Started
        </a>

    </div>

    <div class="floating-scene">

        <div class="book book1">📚</div>
        <div class="book book2">📖</div>
        <div class="student-3d">👨‍🎓</div>
        <div class="teacher-3d">👨‍🏫</div>

        <div class="orb orb1"></div>
        <div class="orb orb2"></div>

    </div>

</section>


<section class="requirement" id="requirement">

    <div class="section-title">
        <span>STEP 01</span>
        <h2>What are you looking for?</h2>
        <p>Select one option to continue.</p>
    </div>

    <div class="choice-container">

        <a href="student-form.php" class="choice-card">

            <div class="choice-icon">👨‍🎓</div>

            <h3>I Need a Teacher</h3>

            <p>
                Looking for a teacher for yourself or your child?
            </p>

            <span class="arrow">→</span>

        </a>


        <a href="teacher-form.php" class="choice-card">

            <div class="choice-icon">👨‍🏫</div>

            <h3>I Need a Student</h3>

            <p>
                Are you a teacher looking for students?
            </p>

            <span class="arrow">→</span>

        </a>

    </div>

</section>


<section class="how" id="how">

    <div class="section-title">

        <span>HOW IT WORKS</span>

        <h2>Simple & Personal</h2>

    </div>


    <div class="steps">

        <div class="step">
            <div>01</div>
            <h3>Submit Details</h3>
            <p>Fill out the appropriate form.</p>
        </div>

        <div class="step">
            <div>02</div>
            <h3>We Review</h3>
            <p>Our team checks the requirement.</p>
        </div>

        <div class="step">
            <div>03</div>
            <h3>We Match</h3>
            <p>We manually select a suitable teacher or student.</p>
        </div>

    </div>

</section>


<section class="privacy" id="about">

    <h2>Your Information Stays Private</h2>

    <p>
        Registration information is collected for matching purposes
        and is accessible only to the authorized administrator.
    </p>

</section>


<footer>

    <div class="logo">Edu<span>Match</span></div>

    <p>Teacher & Student Matching Platform</p>

</footer>


<script src="script.js"></script>

</body>
</html>
<!DOCTYPE html>
<html lang="en">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Find a Teacher</title>

<link rel="stylesheet" href="style.css">

</head>

<body>

<div class="form-page">

    <div class="form-box">

        <a href="index.php" class="back">← Back</a>

        <div class="form-icon">👨‍🎓</div>

        <h1>I Need a Teacher</h1>

        <p>
            Tell us about the student and teacher requirement.
        </p>


        <form action="submit-student.php" method="POST">

            <label>Parent Name</label>
            <input
                type="text"
                name="parent_name"
                required
                placeholder="Enter parent name"
            >


            <label>Student Name</label>
            <input
                type="text"
                name="student_name"
                required
                placeholder="Enter student name"
            >


            <label>Mobile Number</label>
            <input
                type="tel"
                name="mobile"
                required
                pattern="[0-9]{10}"
                placeholder="10 digit mobile number"
            >


            <label>Student Class</label>
            <input
                type="text"
                name="student_class"
                required
                placeholder="Example: Class 8"
            >


            <label>Subject Required</label>
            <input
                type="text"
                name="subject"
                required
                placeholder="Example: Mathematics"
            >


            <label>Board</label>

            <select name="board">

                <option value="">Select Board</option>

                <option>CBSE</option>
                <option>ICSE</option>
                <option>UP Board</option>
                <option>ISC</option>
                <option>Other</option>

            </select>


            <label>Area / Location</label>

            <input
                type="text"
                name="area"
                placeholder="Example: Kakadeo, Kanpur"
            >


            <label>Preferred Time</label>

            <input
                type="text"
                name="preferred_time"
                placeholder="Example: 5 PM - 7 PM"
            >


            <label>Mode</label>

            <select name="mode">

                <option value="">Select Mode</option>

                <option>Offline</option>
                <option>Online</option>
                <option>Both</option>

            </select>


            <label>Special Requirement</label>

            <textarea
                name="special_requirement"
                placeholder="Any important requirement..."
            ></textarea>


            <button type="submit">
                Submit Requirement →
            </button>

        </form>

    </div>

</div>

</body>
</html>
<?php

require_once "config.php";

if ($_SERVER["REQUEST_METHOD"] !== "POST") {
    header("Location: index.php");
    exit;
}

$parent_name = trim($_POST["parent_name"] ?? "");
$student_name = trim($_POST["student_name"] ?? "");
$mobile = trim($_POST["mobile"] ?? "");
$student_class = trim($_POST["student_class"] ?? "");
$subject = trim($_POST["subject"] ?? "");
$board = trim($_POST["board"] ?? "");
$area = trim($_POST["area"] ?? "");
$preferred_time = trim($_POST["preferred_time"] ?? "");
$mode = trim($_POST["mode"] ?? "");
$special_requirement = trim($_POST["special_requirement"] ?? "");

if (
    empty($parent_name) ||
    empty($student_name) ||
    empty($mobile) ||
    empty($student_class) ||
    empty($subject)
) {
    die("Please fill all required fields.");
}

if (!preg_match("/^[0-9]{10}$/", $mobile)) {
    die("Invalid mobile number.");
}


$stmt = $conn->prepare(
    "INSERT INTO student_requirements
    (parent_name, student_name, mobile, student_class, subject, board,
     area, preferred_time, mode, special_requirement)
    VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?)"
);

$stmt->bind_param(
    "ssssssssss",
    $parent_name,
    $student_name,
    $mobile,
    $student_class,
    $subject,
    $board,
    $area,
    $preferred_time,
    $mode,
    $special_requirement
);

if ($stmt->execute()) {

    echo "
    <html>
    <head>
    <link rel='stylesheet' href='style.css'>
    </head>
    <body>

    <div class='success-page'>

        <div class='success-icon'>✓</div>

        <h1>Requirement Submitted!</h1>

        <p>
        Thank you. Your requirement has been successfully submitted.
        Our team will contact you after reviewing your requirement.
        </p>

        <a href='index.php' class='main-btn'>
        Back to Home
        </a>

    </div>

    </body>
    </html>
    ";

} else {

    echo "Something went wrong. Please try again.";

}

$stmt->close();
$conn->close();

?>
<!DOCTYPE html>
<html lang="en">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Teacher Registration</title>

<link rel="stylesheet" href="style.css">

</head>

<body>

<div class="form-page">

<div class="form-box">

<a href="index.php" class="back">← Back</a>

<div class="form-icon">👨‍🏫</div>

<h1>I Need a Student</h1>

<p>
Register as a teacher and our team will contact you for suitable opportunities.
</p>


<form
action="submit-teacher.php"
method="POST"
enctype="multipart/form-data"
>


<label>Teacher Name</label>

<input
type="text"
name="teacher_name"
required
placeholder="Enter your full name"
>


<label>Mobile Number</label>

<input
type="tel"
name="mobile"
required
pattern="[0-9]{10}"
placeholder="10 digit mobile number"
>


<label>Email</label>

<input
type="email"
name="email"
placeholder="Enter email address"
>


<label>Qualification</label>

<input
type="text"
name="qualification"
placeholder="Example: B.Sc, B.Ed, M.Sc"
>


<label>Subjects</label>

<input
type="text"
name="subjects"
required
placeholder="Example: Mathematics, Science"
>


<label>Classes / Grades</label>

<input
type="text"
name="classes"
required
placeholder="Example: Class 6 - 10"
>


<label>Board</label>

<select name="board">

<option value="">Select Board</option>

<option>CBSE</option>
<option>ICSE</option>
<option>ISC</option>
<option>UP Board</option>
<option>Other</option>

</select>


<label>Teaching Experience</label>

<input
type="text"
name="experience"
placeholder="Example: 3 years"
>


<label>Teaching Area</label>

<input
type="text"
name="teaching_area"
placeholder="Example: Kakadeo, Kanpur"
>


<label>Additional Information</label>

<textarea
name="additional_information"
placeholder="Tell us anything important about your teaching..."
></textarea>


<div class="upload-section">

<h3>Document Verification</h3>

<p>
These documents are private and will only be accessible to the administrator.
</p>


<label>Class 10 Marksheet</label>

<input
type="file"
name="class10_marksheet"
accept=".jpg,.jpeg,.png,.pdf"
required
>


<label>Class 12 Marksheet</label>

<input
type="file"
name="class12_marksheet"
accept=".jpg,.jpeg,.png,.pdf"
required
>


<label>Aadhaar / Masked Aadhaar</label>

<input
type="file"
name="aadhaar_document"
accept=".jpg,.jpeg,.png,.pdf"
required
>

</div>


<button type="submit">
Register as Teacher →
</button>

</form>

</div>

</div>

</body>

</html>
<?php

require_once "config.php";

if ($_SERVER["REQUEST_METHOD"] !== "POST") {
    header("Location: index.php");
    exit;
}


$teacher_name = trim($_POST["teacher_name"] ?? "");
$mobile = trim($_POST["mobile"] ?? "");
$email = trim($_POST["email"] ?? "");
$qualification = trim($_POST["qualification"] ?? "");
$subjects = trim($_POST["subjects"] ?? "");
$classes = trim($_POST["classes"] ?? "");
$board = trim($_POST["board"] ?? "");
$experience = trim($_POST["experience"] ?? "");
$teaching_area = trim($_POST["teaching_area"] ?? "");
$additional_information = trim($_POST["additional_information"] ?? "");


if (
    empty($teacher_name) ||
    empty($mobile) ||
    empty($subjects) ||
    empty($classes)
) {
    die("Please fill all required fields.");
}


if (!preg_match("/^[0-9]{10}$/", $mobile)) {
    die("Invalid mobile number.");
}


$uploadDir = __DIR__ . "/private_uploads/";


if (!is_dir($uploadDir)) {
    mkdir($uploadDir, 0700, true);
}


function uploadDocument($file, $uploadDir, $prefix)
{
    if (!isset($file) || $file["error"] !== UPLOAD_ERR_OK) {
        die("Document upload failed.");
    }


    $allowed = [
        "image/jpeg",
        "image/png",
        "application/pdf"
    ];


    if (!in_array($file["type"], $allowed)) {
        die("Only JPG, PNG and PDF files are allowed.");
    }


    if ($file["size"] > 5 * 1024 * 1024) {
        die("File size must be less than 5 MB.");
    }


    $extension = strtolower(
        pathinfo($file["name"], PATHINFO_EXTENSION)
    );


    $filename =
        $prefix . "_" .
        bin2hex(random_bytes(16)) .
        "." . $extension;


    $destination = $uploadDir . $filename;


    if (!move_uploaded_file($file["tmp_name"], $destination)) {
        die("Unable to save uploaded document.");
    }


    return $filename;
}


$class10 = uploadDocument(
    $_FILES["class10_marksheet"],
    $uploadDir,
    "class10"
);


$class12 = uploadDocument(
    $_FILES["class12_marksheet"],
    $uploadDir,
    "class12"
);


$aadhaar = uploadDocument(
    $_FILES["aadhaar_document"],
    $uploadDir,
    "aadhaar"
);


$stmt = $conn->prepare(
    "INSERT INTO teachers
    (teacher_name, mobile, email, qualification, subjects, classes,
     board, experience, teaching_area, additional_information,
     class10_marksheet, class12_marksheet, aadhaar_document)
     VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?)"
);


$stmt->bind_param(
    "sssssssssssss",
    $teacher_name,
    $mobile,
    $email,
    $qualification,
    $subjects,
    $classes,
    $board,
    $experience,
    $teaching_area,
    $additional_information,
    $class10,
    $class12,
    $aadhaar
);


if ($stmt->execute()) {

echo "
<html>
<head>
<link rel='stylesheet' href='style.css'>
</head>

<body>

<div class='success-page'>

<div class='success-icon'>✓</div>

<h1>Registration Successful!</h1>

<p>
Your teacher registration has been received.
Our team will review your information and contact you.
</p>

<a href='index.php' class='main-btn'>
Back to Home
</a>

</div>

</body>
</html>
";

} else {

echo "Registration failed.";

}


$stmt->close();
$conn->close();

?>
<?php

require_once "../config.php";

if (isset($_SESSION["admin_logged_in"])) {
    header("Location: dashboard.php");
    exit;
}


$error = "";


if ($_SERVER["REQUEST_METHOD"] === "POST") {

    $username = $_POST["username"] ?? "";
    $password = $_POST["password"] ?? "";


    $stmt = $conn->prepare(
        "SELECT id, username, password
         FROM admin
         WHERE username = ?
         LIMIT 1"
    );


    $stmt->bind_param("s", $username);

    $stmt->execute();

    $result = $stmt->get_result();


    if ($result->num_rows === 1) {

        $admin = $result->fetch_assoc();


        if (password_verify($password, $admin["password"])) {

            $_SESSION["admin_logged_in"] = true;
            $_SESSION["admin_id"] = $admin["id"];

            header("Location: dashboard.php");
            exit;

        }

    }


    $error = "Invalid username or password.";
}

?>


<!DOCTYPE html>

<html>

<head>

<meta charset="UTF-8">

<meta name="viewport"
content="width=device-width, initial-scale=1.0">

<title>Admin Login</title>

<link rel="stylesheet" href="style.css">

</head>


<body>

<div class="admin-login">

<div class="login-box">

<h1>Admin Login</h1>

<p>Private Administration Panel</p>


<?php if ($error): ?>

<div class="error">
<?= htmlspecialchars($error) ?>
</div>

<?php endif; ?>


<form method="POST">

<input
type="text"
name="username"
placeholder="Username"
required
>


<input
type="password"
name="password"
placeholder="Password"
required
>


<button type="submit">
Login
</button>

</form>

</div>

</div>

</body>

</html>
<?php

require_once "../config.php";


if (!isset($_SESSION["admin_logged_in"])) {

    header("Location: login.php");

    exit;

}


$students = $conn->query(
    "SELECT * FROM student_requirements
     ORDER BY created_at DESC"
);


$teachers = $conn->query(
    "SELECT * FROM teachers
     ORDER BY created_at DESC"
);

?>


<!DOCTYPE html>

<html>

<head>

<meta charset="UTF-8">

<meta name="viewport"
content="width=device-width, initial-scale=1.0">

<title>Admin Dashboard</title>

<link rel="stylesheet" href="style.css">

</head>


<body>


<header class="admin-header">

<div>

<h1>EduMatch Admin</h1>

<p>Private Management Dashboard</p>

</div>


<a href="logout.php">
Logout
</a>

</header>


<main class="dashboard">


<section>

<h2>👨‍🎓 Teacher Requirements</h2>


<div class="table-container">

<table>

<tr>

<th>Name</th>
<th>Student</th>
<th>Mobile</th>
<th>Class</th>
<th>Subject</th>
<th>Board</th>
<th>Area</th>
<th>Time</th>
<th>Mode</th>
<th>Status</th>

</tr>


<?php while ($row = $students->fetch_assoc()): ?>

<tr>

<td>
<?= htmlspecialchars($row["parent_name"]) ?>
</td>

<td>
<?= htmlspecialchars($row["student_name"]) ?>
</td>

<td>
<?= htmlspecialchars($row["mobile"]) ?>
</td>

<td>
<?= htmlspecialchars($row["student_class"]) ?>
</td>

<td>
<?= htmlspecialchars($row["subject"]) ?>
</td>

<td>
<?= htmlspecialchars($row["board"]) ?>
</td>

<td>
<?= htmlspecialchars($row["area"]) ?>
</td>

<td>
<?= htmlspecialchars($row["preferred_time"]) ?>
</td>

<td>
<?= htmlspecialchars($row["mode"]) ?>
</td>

<td>
<?= htmlspecialchars($row["status"]) ?>
</td>

</tr>

<?php endwhile; ?>


</table>

</div>

</section>



<section>

<h2>👨‍🏫 Teacher Registrations</h2>


<div class="table-container">

<table>

<tr>

<th>Name</th>
<th>Mobile</th>
<th>Email</th>
<th>Qualification</th>
<th>Subjects</th>
<th>Classes</th>
<th>Board</th>
<th>Experience</th>
<th>Area</th>
<th>Documents</th>
<th>Status</th>

</tr>


<?php while ($row = $teachers->fetch_assoc()): ?>

<tr>

<td>
<?= htmlspecialchars($row["teacher_name"]) ?>
</td>

<td>
<?= htmlspecialchars($row["mobile"]) ?>
</td>

<td>
<?= htmlspecialchars($row["email"]) ?>
</td>

<td>
<?= htmlspecialchars($row["qualification"]) ?>
</td>

<td>
<?= htmlspecialchars($row["subjects"]) ?>
</td>

<td>
<?= htmlspecialchars($row["classes"]) ?>
</td>

<td>
<?= htmlspecialchars($row["board"]) ?>
</td>

<td>
<?= htmlspecialchars($row["experience"]) ?>
</td>

<td>
<?= htmlspecialchars($row["teaching_area"]) ?>
</td>

<td>

<span>10th ✓</span><br>
<span>12th ✓</span><br>
<span>Aadhaar ✓</span>

</td>

<td>
<?= htmlspecialchars($row["status"]) ?>
</td>

</tr>

<?php endwhile; ?>


</table>

</div>

</section>


</main>

</body>

</html>
<?php

require_once "../config.php";

session_destroy();

header("Location: login.php");

exit;

?>
Order Allow,Deny
Deny from all
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: Arial, sans-serif;
    background: #f7f9fc;
    color: #172033;
}

header {
    width: 100%;
    padding: 20px 8%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: white;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 5px 20px rgba(0,0,0,.05);
}

.logo {
    font-size: 26px;
    font-weight: 800;
}

.logo span {
    color: #5b5ff0;
}

nav {
    display: flex;
    gap: 30px;
}

nav a {
    text-decoration: none;
    color: #172033;
    font-weight: 600;
}

.hero {
    min-height: 650px;
    padding: 80px 8%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    overflow: hidden;
    background:
        radial-gradient(circle at 80% 20%, #e4e5ff, transparent 35%),
        #f7f9fc;
}

.hero-content {
    width: 50%;
}

.badge {
    display: inline-block;
    padding: 10px 16px;
    border-radius: 30px;
    background: #e9e9ff;
    color: #5558d9;
    font-weight: 600;
    margin-bottom: 20px;
}

.hero h1 {
    font-size: 58px;
    line-height: 1.05;
    margin-bottom: 25px;
}

.hero h1 span {
    color: #5b5ff0;
    display: block;
}

.hero p {
    font-size: 19px;
    line-height: 1.7;
    max-width: 600px;
    color: #667085;
    margin-bottom: 35px;
}

.main-btn {
    display: inline-block;
    text-decoration: none;
    background: #5b5ff0;
    color: white;
    padding: 15px 28px;
    border-radius: 12px;
    font-weight: 700;
    transition: .3s;
}

.main-btn:hover {
    transform: translateY(-4px);
}

.floating-scene {
    width: 420px;
    height: 420px;
    position: relative;
}

.student-3d,
.teacher-3d {
    position: absolute;
    font-size: 120px;
    animation: float 4s ease-in-out infinite;
}

.student-3d {
    left: 30px;
    top: 130px;
}

.teacher-3d {
    right: 20px;
    top: 50px;
    animation-delay: 1s;
}

.book {
    position: absolute;
    font-size: 55px;
    animation: float 3s ease-in-out infinite;
}

.book1 {
    left: 150px;
    top: 30px;
}

.book2 {
    right: 100px;
    bottom: 60px;
}

.orb {
    width: 80px;
    height: 80px;
    position: absolute;
    border-radius: 50%;
    background: linear-gradient(135deg, #6d70ff, #b5b7ff);
    opacity: .4;
    animation: float 5s infinite;
}

.orb1 {
    left: 10px;
    bottom: 40px;
}

.orb2 {
    right: 0;
    top: 10px;
}

@keyframes float {

    0%,100% {
        transform: translateY(0) rotate(0deg);
    }

    50% {
        transform: translateY(-20px) rotate(5deg);
    }
}

.requirement,
.how {
    padding: 100px 8%;
    background: white;
}

.section-title {
    text-align: center;
    margin-bottom: 50px;
}

.section-title span {
    color: #5b5ff0;
    font-weight: 800;
    font-size: 13px;
}

.section-title h2 {
    font-size: 40px;
    margin: 12px 0;
}

.section-title p {
    color: #667085;
}

.choice-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
    max-width: 1000px;
    margin: auto;
}

.choice-card {
    position: relative;
    padding: 45px;
    text-decoration: none;
    color: #172033;
    border: 1px solid #e6e8ef;
    border-radius: 25px;
    transition: .35s;
    background: white;
}

.choice-card:hover {
    transform: translateY(-12px) rotateX(2deg);
    box-shadow: 0 25px 60px rgba(50,50,100,.12);
}

.choice-icon {
    font-size: 65px;
    margin-bottom: 20px;
}

.choice-card h3 {
    font-size: 27px;
    margin-bottom: 12px;
}

.choice-card p {
    color: #667085;
    line-height: 1.6;
}

.arrow {
    position: absolute;
    right: 30px;
    bottom: 30px;
    font-size: 30px;
    color: #5b5ff0;
}

.steps {
    display: grid;
    grid-template-columns: repeat(3,1fr);
    gap: 30px;
    max-width: 1000px;
    margin: auto;
}

.step {
    text-align: center;
    padding: 30px;
}

.step > div {
    width: 65px;
    height: 65px;
    border-radius: 50%;
    display: grid;
    place-items: center;
    background: #e9e9ff;
    color: #5b5ff0;
    font-weight: 800;
    margin: auto auto 20px;
}

.step h3 {
    margin-bottom: 10px;
}

.step p {
    color: #667085;
}

.privacy {
    padding: 80px 8%;
    text-align: center;
    background: #15182b;
    color: white;
}

.privacy p {
    max-width: 650px;
    margin: 15px auto;
    line-height: 1.7;
    color: #c5c8d5;
}

footer {
    padding: 30px 8%;
    display: flex;
    justify-content: space-between;
    background: white;
}


/* FORM */

.form-page {
    min-height: 100vh;
    padding: 50px 20px;
    background:
        radial-gradient(circle at 10% 10%, #e6e7ff, transparent 30%),
        #f7f9fc;
}

.form-box {
    max-width: 700px;
    margin: auto;
    background: white;
    padding: 45px;
    border-radius: 25px;
    box-shadow: 0 20px 60px rgba(0,0,0,.08);
}

.back {
    text-decoration: none;
    color: #5b5ff0;
}

.form-icon {
    font-size: 65px;
    margin-top: 25px;
}

.form-box h1 {
    font-size: 38px;
    margin: 10px 0;
}

.form-box > p {
    color: #667085;
    margin-bottom: 30px;
}

form label {
    display: block;
    margin: 20px 0 8px;
    font-weight: 700;
}

input,
select,
textarea {
    width: 100%;
    padding: 14px 16px;
    border: 1px solid #dfe2ea;
    border-radius: 10px;
    outline: none;
    font-size: 15px;
}

input:focus,
select:focus,
textarea:focus {
    border-color: #5b5ff0;
}

textarea {
    min-height: 120px;
    resize: vertical;
}

form button {
    width: 100%;
    border: 0;
    margin-top: 30px;
    padding: 16px;
    border-radius: 12px;
    background: #5b5ff0;
    color: white;
    font-size: 16px;
    font-weight: 800;
    cursor: pointer;
}

.upload-section {
    margin-top: 35px;
    padding: 25px;
    border-radius: 15px;
    background: #f5f6ff;
}

.upload-section h3 {
    margin-bottom: 10px;
}

.upload-section p {
    color: #667085;
    font-size: 14px;
}


/* SUCCESS */

.success-page {
    min-height: 100vh;
    display: grid;
    place-items: center;
    text-align: center;
    padding: 30px;
}

.success-icon {
    width: 90px;
    height: 90px;
    border-radius: 50%;
    background: #dff8e7;
    color: #20a05a;
    display: grid;
    place-items: center;
    font-size: 45px;
    margin: auto auto 20px;
}

.success-page p {
    max-width: 550px;
    color: #667085;
    line-height: 1.7;
    margin: 15px auto 30px;
}


/* MOBILE */

@media(max-width:800px) {

    header {
        padding: 18px 5%;
    }

    nav {
        display: none;
    }

    .hero {
        flex-direction: column;
        text-align: center;
        padding: 70px 5%;
    }

    .hero-content {
        width: 100%;
    }

    .hero h1 {
        font-size: 42px;
    }

    .hero p {
        font-size: 16px;
    }

    .floating-scene {
        width: 320px;
        height: 300px;
        margin-top: 40px;
    }

    .student-3d,
    .teacher-3d {
        font-size: 85px;
    }

    .choice-container,
    .steps {
        grid-template-columns: 1fr;
    }

    .form-box {
        padding: 28px 20px;
    }

    footer {
        flex-direction: column;
        gap: 10px;
    }
}
const cards = document.querySelectorAll(".choice-card");

cards.forEach(card => {

    card.addEventListener("mousemove", function(e) {

        const rect = card.getBoundingClientRect();

        const x = e.clientX - rect.left;
        const y = e.clientY - rect.top;

        const centerX = rect.width / 2;
        const centerY = rect.height / 2;

        const rotateX = (y - centerY) / 25;
        const rotateY = (centerX - x) / 25;

        card.style.transform =
            `perspective(800px)
             rotateX(${rotateX}deg)
             rotateY(${rotateY}deg)
             translateY(-8px)`;

    });


    card.addEventListener("mouseleave", function() {

        card.style.transform =
            "perspective(800px) rotateX(0) rotateY(0) translateY(0)";

    });

});
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f5f7fb;
    color: #172033;
}

.admin-header {
    padding: 25px 5%;
    background: #15182b;
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.admin-header a {
    color: white;
    text-decoration: none;
    background: #5b5ff0;
    padding: 10px 20px;
    border-radius: 8px;
}

.dashboard {
    padding: 40px 5%;
}

.dashboard section {
    background: white;
    padding: 25px;
    border-radius: 15px;
    margin-bottom: 40px;
}

.table-container {
    overflow-x: auto;
}

table {
    width: 100%;
    border-collapse: collapse;
    min-width: 1000px;
}

th,
td {
    padding: 13px;
    border-bottom: 1px solid #eee;
    text-align: left;
    font-size: 14px;
}

th {
    background: #f5f6ff;
}

.admin-login {
    min-height: 100vh;
    display: grid;
    place-items: center;
    background: #f5f7fb;
}

.login-box {
    background: white;
    width: 380px;
    max-width: 90%;
    padding: 35px;
    border-radius: 18px;
    box-shadow: 0 20px 60px rgba(0,0,0,.1);
}

.login-box input {
    width: 100%;
    padding: 14px;
    margin: 10px 0;
    box-sizing: border-box;
}

.login-box button {
    width: 100%;
    padding: 14px;
    background: #5b5ff0;
    color: white;
    border: 0;
    border-radius: 8px;
    margin-top: 15px;
}

.error {
    background: #ffe5e5;
    color: #b00020;
    padding: 10px;
    border-radius: 8px;
}
