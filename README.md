<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PRINCE TITUS GENERAL HOSPITAL MANAGEMENT SYSTEM</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f0f8ff;
            color: #333;
            margin: 0;
            padding: 0;
        }

        h1, h2, h3 {
            color: #2e8b57;
        }

        header {
            background-color: #2e8b57;
            color: white;
            text-align: center;
            padding: 20px 0;
        }

        .container {
            padding: 20px;
        }

        .section {
            margin-bottom: 40px;
            padding: 20px;
            background-color: #fff;
            border: 1px solid #ccc;
            border-radius: 8px;
            box-shadow: 0px 0px 10px rgba(0,0,0,0.1);
        }

        .section h2 {
            border-bottom: 2px solid #2e8b57;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }

        input, select, textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        button {
            background-color: #2e8b57;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #3e9f67;
        }

        table {
            width: 100%;
            margin-bottom: 20px;
            border-collapse: collapse;
        }

        table, th, td {
            border: 1px solid #ddd;
        }

        th, td {
            padding: 10px;
            text-align: left;
        }

        .receipt {
            display: none;
            margin-top: 20px;
            padding: 20px;
            background-color: #f5f5f5;
            border: 1px solid #ddd;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }

        .total {
            text-align: right;
            font-size: 1.2em;
            margin-top: 20px;
        }

        .footer {
            text-align: center;
            padding: 20px;
            background-color: #2e8b57;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

        .logo {
            width: 120px;
        }

        .footer img {
            width: 50px;
        }
    </style>
</head>
<body>

<header>
    <img src="hospital_logo.png" alt="Hospital Logo" class="logo">
    <p>PRINCE TITUS GENERAL HOSPITAL MANAGEMENT SYSTEM</p>
    <p>Your Health, Our Priority</p>
</header>

<div class="container">

    <!-- Patient Registration Section -->
    <div class="section" id="patient-registration">
        <h2>Patient Registration</h2>
        <form>
            <label for="patientName">Name:</label>
            <input type="text" id="patientName">

            <label for="patientAge">Age:</label>
            <input type="number" id="patientAge">

            <label for="patientGender">Gender:</label>
            <select id="patientGender">
                <option value="Male">Male</option>
                <option value="Female">Female</option>
            </select>

            <label for="patientCondition">Condition:</label>
            <textarea id="patientCondition"></textarea>

            <label for="assignedDoctor">Doctor Assigned:</label>
            <input type="text" id="assignedDoctor">

            <button type="button" onclick="registerPatient()">Register Patient</button>
        </form>
    </div>

    <!-- Consultation Room Section -->
    <div class="section" id="consultation">
        <h2>Consultation Room</h2>
        <button type="button" onclick="proceedToLab()">Send Patient to Lab</button>
    </div>

    <!-- Lab Section -->
    <div class="section" id="lab">
        <h2>Lab Tests</h2>
        <form>
            <label for="labTests">Lab Tests Required:</label>
            <input type="text" id="labTests">
            <button type="button" onclick="proceedToOrthopedics()">Send to Orthopedics</button>
        </form>
    </div>

    <!-- Orthopedics Section -->
    <div class="section" id="orthopedics">
        <h2>Orthopedics</h2>
        <form>
            <label for="orthopedicsTreatment">Orthopedic Treatment:</label>
            <input type="text" id="orthopedicsTreatment">
            <button type="button" onclick="proceedToInjectionRoom()">Send to Injection Room</button>
        </form>
    </div>

    <!-- Injection Room Section -->
    <div class="section" id="injection-room">
        <h2>Injection Room</h2>
        <form>
            <label for="injection">Injection Administered:</label>
            <input type="text" id="injection">
            <button type="button" onclick="completeTreatment()">Complete Treatment</button>
        </form>
    </div>

</div>

<footer class="footer">
  
</footer>

<script>
// Store data temporarily for use across services
let patientData = {};

// Register the patient and store their data
function registerPatient() {
    const name = document.getElementById('patientName').value;
    const age = document.getElementById('patientAge').value;
    const gender = document.getElementById('patientGender').value;
    const condition = document.getElementById('patientCondition').value;
    const doctor = document.getElementById('assignedDoctor').value;

    patientData = {
        name: name,
        age: age,
        gender: gender,
        condition: condition,
        doctor: doctor
    };

    alert(`Patient Registered: \nName: ${name}\nAge: ${age}\nGender: ${gender}\nCondition: ${condition}\nAssigned Doctor: ${doctor}`);
}

// Proceed from Consultation Room to Lab
function proceedToLab() {
    alert(`Sending ${patientData.name} to Lab for further tests.`);
}

// Proceed from Lab to Orthopedics
function proceedToOrthopedics() {
    const labTests = document.getElementById('labTests').value;
    patientData.labTests = labTests;
    alert(`Lab Tests for ${patientData.name}: ${labTests}\nSending to Orthopedics.`);
}

// Proceed from Orthopedics to Injection Room
function proceedToInjectionRoom() {
    const orthopedicsTreatment = document.getElementById('orthopedicsTreatment').value;
    patientData.orthopedicsTreatment = orthopedicsTreatment;
    alert(`Orthopedic Treatment for ${patientData.name}: ${orthopedicsTreatment}\nSending to Injection Room.`);
}

// Complete Treatment in the Injection Room
function completeTreatment() {
    const injection = document.getElementById('injection').value;
    patientData.injection = injection;
    alert(`Injection Administered: ${injection}\nTreatment Completed for ${patientData.name}.`);
}
</script>

</body>
</html>
