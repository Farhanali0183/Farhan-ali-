<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Premium Dental Lab System</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.4.0/css/all.min.css">
  <style>
    .premium-page {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      min-height: 100vh;
    }
    
    .doctor-card {
      background: white;
      border-radius: 15px;
      padding: 20px;
      margin: 10px 0;
      box-shadow: 0 4px 15px rgba(0,0,0,0.1);
      transition: all 0.3s ease;
      cursor: pointer;
    }
    
    .doctor-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 25px rgba(0,0,0,0.15);
    }
    
    .fab-button {
      position: fixed;
      bottom: 30px;
      right: 30px;
      width: 60px;
      height: 60px;
      background: linear-gradient(45deg, #2ecc71, #27ae60);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 24px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(46, 204, 113, 0.3);
      transition: all 0.3s ease;
      z-index: 1000;
    }
    
    .fab-button:hover {
      transform: scale(1.1);
      box-shadow: 0 12px 30px rgba(46, 204, 113, 0.4);
    }
    
    .lab-name-editable {
      background: transparent;
      border: none;
      color: white;
      font-size: 2rem;
      font-weight: bold;
      text-align: center;
      width: 100%;
      padding: 10px;
    }
    
    .lab-name-editable:focus {
      outline: none;
      border-bottom: 2px dashed rgba(255,255,255,0.5);
    }
    
    .search-bar {
      background: rgba(255,255,255,0.2);
      border: none;
      border-radius: 25px;
      padding: 15px 20px;
      color: white;
      width: 100%;
      backdrop-filter: blur(10px);
    }
    
    .search-bar::placeholder {
      color: rgba(255,255,255,0.7);
    }
    
    .search-bar:focus {
      outline: none;
      background: rgba(255,255,255,0.3);
    }
    
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 2000;
    }
    
    .modal-content {
      background: white;
      border-radius: 20px;
      padding: 30px;
      width: 90%;
      max-width: 400px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.2);
    }
    
    .premium-input {
      width: 100%;
      padding: 15px;
      border: 2px solid #e0e0e0;
      border-radius: 10px;
      margin: 10px 0;
      font-size: 16px;
      transition: border-color 0.3s ease;
    }
    
    .premium-input:focus {
      outline: none;
      border-color: #667eea;
    }
    
    .premium-button {
      background: linear-gradient(45deg, #667eea, #764ba2);
      color: white;
      border: none;
      padding: 15px 30px;
      border-radius: 10px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s ease;
      width: 100%;
      margin: 10px 0;
    }
    
    .premium-button:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 20px rgba(102, 126, 234, 0.3);
    }
    
    .bill-maker-section {
      display: none;
    }
    
    /* Original bill maker styles */
    .bill-maker-section body {
      font-family: Arial, sans-serif;
      margin: 20px;
      background-color: #f5f5f5;
    }
    .bill-maker-section .header {
      background-color: #3498db;
      color: white;
      padding: 15px;
      text-align: center;
      border-radius: 5px;
      margin-bottom: 20px;
      position: relative;
      border: 1px solid #2980b9;
    }
    .bill-maker-section .logo {
      position: absolute;
      left: 20px;
      top: 15px;
      width: 50px;
      height: 50px;
      background: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 24px;
      border: 1px solid #ddd;
    }
    .bill-maker-section table {
      width: 100%;
      border-collapse: collapse;
      margin-bottom: 20px;
      border: 1px solid #ddd;
    }
    .bill-maker-section th {
      background-color: #2980b9;
      color: white;
      padding: 10px;
      text-align: left;
      border: 1px solid #ddd;
    }
    .bill-maker-section td {
      padding: 10px;
      border-bottom: 1px solid #ddd;
      border-right: 1px solid #ddd;
    }
    .bill-maker-section tr:nth-child(even) {
      background-color: #f2f2f2;
    }
    .bill-maker-section .summary-box {
      background-color: white;
      padding: 20px;
      border-radius: 5px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      margin-top: 20px;
      border: 1px solid #ddd;
    }
    .bill-maker-section .summary-box p {
      display: flex;
      justify-content: space-between;
      margin: 10px 0;
    }
    .bill-maker-section button {
      background-color: #27ae60;
      color: white;
      border: none;
      padding: 10px 15px;
      border-radius: 5px;
      cursor: pointer;
      margin-right: 10px;
      margin-top: 10px;
    }
    .bill-maker-section button:hover {
      background-color: #219653;
    }
    .bill-maker-section input, .bill-maker-section select {
      padding: 5px;
      border: 1px solid #ddd;
      border-radius: 3px;
    }
    .bill-maker-section .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.5);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }
    .bill-maker-section .modal-content {
      background-color: white;
      padding: 20px;
      border-radius: 5px;
      width: 90%;
      max-width: 500px;
      border: 1px solid #ddd;
    }
    .bill-maker-section .product-btn {
      background-color: #f39c12;
    }
    .bill-maker-section .view-bills-btn {
      background-color: #9b59b6;
    }
    .bill-maker-section .save-section {
      background-color: #ecf0f1;
      padding: 20px;
      border-radius: 5px;
      margin-top: 20px;
      text-align: center;
      display: none;
      border: 1px solid #ddd;
    }
    .bill-maker-section .form-row {
      margin-bottom: 15px;
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
    }
    .bill-maker-section .form-row label {
      display: flex;
      align-items: center;
      gap: 5px;
    }
    .bill-maker-section .doctor-info {
      color: #2c3e50;
      font-weight: bold;
    }
    .bill-maker-section .date-info {
      color: #2c3e50;
    }
    .bill-maker-section .premium-text {
      font-weight: bold;
      color: #2980b9;
    }
    .bill-maker-section .teeth-grid {
      display: grid;
      grid-template-columns: repeat(8, 1fr);
      gap: 5px;
      margin: 15px 0;
    }
    .bill-maker-section .tooth-btn {
      padding: 8px;
      border: 1px solid #ddd;
      border-radius: 3px;
      cursor: pointer;
      text-align: center;
    }
    .bill-maker-section .tooth-btn.selected {
      background-color: #3498db;
      color: white;
    }
    .bill-maker-section .lab-name-input {
      background: transparent;
      border: none;
      color: white;
      font-size: 24px;
      text-align: center;
      width: 100%;
      font-weight: bold;
    }
    .bill-maker-section .lab-name-input:focus {
      outline: none;
      border-bottom: 1px dashed white;
    }
    .bill-maker-section .account-hint {
      color: #7f8c8d;
      font-style: italic;
      font-size: 0.9em;
    }
    .bill-maker-section .payment-section {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      margin-top: 15px;
    }
    .bill-maker-section .payment-section label {
      display: flex;
      flex-direction: column;
    }
    
    .watermark {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) rotate(-45deg);
      font-size: 80px;
      color: rgba(102, 126, 234, 0.1);
      z-index: -1;
      pointer-events: none;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <!-- Premium First Page -->
  <div id="premiumPage" class="premium-page">
    <div class="container mx-auto px-4 py-8">
      <!-- Header -->
      <div class="text-center mb-8">
        <div class="flex items-center justify-center mb-4">
          <div class="w-16 h-16 bg-white rounded-full flex items-center justify-center text-3xl mr-4">
            🦷
          </div>
          <input 
            type="text" 
            class="lab-name-editable" 
            id="premiumLabName" 
            value="GOOD SMILE DENTAL LAB"
            placeholder="Enter Lab Name"
          >
        </div>
        <p class="text-white text-lg opacity-90">Quality Dental Products</p>
      </div>
      
      <!-- Search Bar -->
      <div class="mb-8">
        <div class="relative">
          <input 
            type="text" 
            class="search-bar" 
            id="doctorSearch" 
            placeholder="Search doctors..."
            onkeyup="searchDoctors()"
          >
          <i class="fas fa-search absolute right-5 top-1/2 transform -translate-y-1/2 text-white opacity-70"></i>
        </div>
      </div>
      
      <!-- Saved Doctors -->
      <div class="mb-8">
        <h2 class="text-white text-2xl font-bold mb-4">
          <i class="fas fa-user-md mr-2"></i>Saved Doctors
        </h2>
        <div id="doctorsList" class="space-y-4">
          <!-- Doctor cards will be inserted here -->
        </div>
        <div id="noDoctors" class="text-center text-white opacity-70 py-8">
          <i class="fas fa-user-plus text-6xl mb-4"></i>
          <p class="text-xl">No doctors saved yet</p>
          <p>Click the + button to add your first doctor</p>
        </div>
      </div>
    </div>
    
    <!-- FAB Button -->
    <div class="fab-button" onclick="openDoctorModal()">
      <i class="fas fa-plus"></i>
    </div>
  </div>
  
  <!-- Add Doctor Modal -->
  <div id="doctorModal" class="modal-overlay" style="display: none;">
    <div class="modal-content">
      <div class="text-center mb-6">
        <h2 class="text-2xl font-bold text-gray-800">Add New Doctor</h2>
        <p class="text-gray-600">Enter doctor information</p>
      </div>
      
      <form id="doctorForm">
        <input 
          type="text" 
          class="premium-input" 
          id="newDoctorName" 
          placeholder="Doctor Name"
          required
        >
        <input 
          type="text" 
          class="premium-input" 
          id="newClinicName" 
          placeholder="Clinic Name"
          required
        >
        <input 
          type="tel" 
          class="premium-input" 
          id="newPhoneNumber" 
          placeholder="Phone Number"
          required
        >
        
        <div class="flex gap-4">
          <button type="submit" class="premium-button">
            <i class="fas fa-save mr-2"></i>Save Doctor
          </button>
          <button type="button" class="premium-button" onclick="closeDoctorModal()" style="background: #e74c3c;">
            <i class="fas fa-times mr-2"></i>Cancel
          </button>
        </div>
      </form>
    </div>
  </div>
  
  <!-- Bill Maker Section (Original Code) -->
  <div id="billMakerSection" class="bill-maker-section">
    <div class="watermark">GOOD SMILE DENTAL LAB</div>
    <div class="header">
      <div class="logo">🦷</div>
      <h1><input type="text" class="lab-name-input" id="labName" value="GOOD SMILE DENTAL LAB"></h1>
      <p class="premium-text">Quality Dental Products</p>
      <button onclick="goBackToPremiumPage()" style="position: absolute; right: 20px; top: 20px; background: #e74c3c; padding: 10px 15px; border-radius: 5px;">
        <i class="fas fa-arrow-left"></i> Back
      </button>
    </div>

    <div class="form-row">
      <label class="doctor-info">Doctor Name: <input type="text" id="doctorName" value="Dr. Ali Sher"></label>
      <label>Bill No: <input type="text" id="billNo" value="420"></label>
      <label class="date-info">Date: <input type="date" id="billDate"></label>
      <label>Month: 
        <select id="monthSelect">
          <option value="January">January</option>
          <option value="February">February</option>
          <option value="March">March</option>
          <option value="April">April</option>
          <option value="May">May</option>
          <option value="June">June</option>
          <option value="July">July</option>
          <option value="August">August</option>
          <option value="September">September</option>
          <option value="October">October</option>
          <option value="November">November</option>
          <option value="December">December</option>
        </select>
      </label>
    </div>

    <table id="billTable">
      <thead>
        <tr>
          <th>ORDER DATE</th>
          <th>CASE NO.</th>
          <th>PRODUCT</th>
          <th>TEETH</th>
          <th>PRICE</th>
          <th>QTY</th>
          <th>TOTAL</th>
        </tr>
      </thead>
      <tbody id="tableBody"></tbody>
    </table>
    <button onclick="addRow()">Add Row</button>

    <div class="summary-box">
      <p>SUB-TOTAL: <span id="subTotal">0.00</span></p>
      <p>PREVIOUS: <input type="number" id="PREVIOUS" value="0" oninput="updateTotals()" style="width:80px; text-align:right;"></p>
      <p>TOTAL BILL: <span id="totalBill">0.00</span></p>
      <p>RECEIVED: <input type="number" id="received" value="0" oninput="updateTotals()" style="width:80px; text-align:right;"></p>
      <p>BALANCE: <span id="balance">0.00</span></p>
    </div>

    <div class="payment-section">
      <label>
        Payment Method: 
        <input type="text" id="paymentMethod" value="Easypaisa & JazzCash">
      </label>
      <label>
        Account No 1: 
        <input type="text" id="accountNo1" placeholder="0343-3778246">
        <span class="account-hint">Format: 0000-0000000</span>
      </label>
      <label>
        Account No 2: 
        <input type="text" id="accountNo2" placeholder="0300-1234567">
        <span class="account-hint">Format: 0000-0000000</span>
      </label>
    </div>

    <div style="margin-top:20px; text-align:center;">
      <button onclick="saveBill()">Save Bill</button>
      <button onclick="generatePDF()" style="background:#e67e22;">Download PDF</button>
      <button onclick="showSavedBills()" class="view-bills-btn">View Saved Bills</button>
    </div>

    <div class="save-section" id="saveSection">
      <h2>Bill Saved Successfully!</h2>
      <p>Bill No: <span id="savedBillNo"></span> | Date: <span id="savedBillDate"></span></p>
      <p>Total Amount: <span id="savedTotal"></span></p>
      <button onclick="resetForm()" style="background:#3498db;">Create New Bill</button>
    </div>

    <!-- Saved Bills Container -->
    <div id="savedBillsContainer" style="display:none; margin-top:20px; background:#ecf0f1; padding:20px; border-radius:5px;">
      <h2>Saved Bills</h2>
      <div id="savedBillsList"></div>
      <button onclick="hideSavedBills()" style="margin-top:15px;">Close</button>
    </div>

    <!-- Product Type Modal -->
    <div id="productModal" class="modal">
      <div class="modal-content">
        <h3 style="text-align:center;">Select Product Type</h3>
        <div style="text-align:center; margin-top:20px;">
          <button onclick="selectProduct('PC')" style="display:block; width:100%; margin-bottom:10px;">PC</button>
          <button onclick="selectProduct('PD')" style="display:block; width:100%; margin-bottom:10px;">PD</button>
          <button onclick="selectCustomProduct()" style="display:block; width:100%; background:#7f8c8d;">Other</button>
        </div>
        <div style="text-align:center; margin-top:20px;">
          <button onclick="closeProductModal()" style="background:#e74c3c;">Cancel</button>
        </div>
      </div>
    </div>

    <!-- Teeth Selection Modal -->
    <div id="teethModal" class="modal">
      <div class="modal-content">
        <h3 style="text-align:center;">Select Teeth</h3>
        <div class="teeth-grid" id="teethSelection">
          <!-- Upper Right -->
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UR1</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UR2</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UR3</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UR4</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UR5</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UR6</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UR7</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UR8</button>
          
          <!-- Upper Left -->
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UL1</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UL2</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UL3</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UL4</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UL5</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UL6</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UL7</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">UL8</button>
          
          <!-- Lower Right -->
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LR1</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LR2</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LR3</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LR4</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LR5</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LR6</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LR7</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LR8</button>
          
          <!-- Lower Left -->
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LL1</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LL2</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LL3</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LL4</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LL5</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LL6</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LL7</button>
          <button class="tooth-btn" onclick="toggleToothSelection(this)">LL8</button>
        </div>
        <div style="text-align:center; margin-top:20px;">
          <button onclick="applyTeethSelection()">Apply</button>
          <button onclick="closeTeethModal()" style="background:#e74c3c;">Cancel</button>
        </div>
      </div>
    </div>
  </div>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.25/jspdf.plugin.autotable.min.js"></script>
  <script>
    // Global variables
    let savedDoctors = JSON.parse(localStorage.getItem('savedDoctors')) || [];
    let currentDoctor = null;
    
    // Premium page functions
    function loadDoctors() {
      const doctorsList = document.getElementById('doctorsList');
      const noDoctors = document.getElementById('noDoctors');
      
      if (savedDoctors.length === 0) {
        doctorsList.innerHTML = '';
        noDoctors.style.display = 'block';
        return;
      }
      
      noDoctors.style.display = 'none';
      doctorsList.innerHTML = '';
      
      savedDoctors.forEach((doctor, index) => {
        const doctorCard = document.createElement('div');
        doctorCard.className = 'doctor-card';
        doctorCard.onclick = () => openBillMaker(doctor);
        
        doctorCard.innerHTML = `
          <div class="flex items-center justify-between">
            <div class="flex items-center">
              <div class="w-12 h-12 bg-gradient-to-r from-blue-500 to-purple-600 rounded-full flex items-center justify-center text-white font-bold text-lg mr-4">
                ${doctor.name.charAt(0)}
              </div>
              <div>
                <h3 class="font-bold text-lg text-gray-800">${doctor.name}</h3>
                <p class="text-gray-600">${doctor.clinic}</p>
                <p class="text-gray-500 text-sm"><i class="fas fa-phone mr-1"></i>${doctor.phone}</p>
              </div>
            </div>
            <div class="flex items-center">
              <i class="fas fa-chevron-right text-gray-400"></i>
            </div>
          </div>
        `;
        
        doctorsList.appendChild(doctorCard);
      });
    }
    
    function searchDoctors() {
      const searchTerm = document.getElementById('doctorSearch').value.toLowerCase();
      const doctorCards = document.querySelectorAll('.doctor-card');
      
      doctorCards.forEach(card => {
        const doctorName = card.querySelector('h3').textContent.toLowerCase();
        const clinicName = card.querySelector('p').textContent.toLowerCase();
        
        if (doctorName.includes(searchTerm) || clinicName.includes(searchTerm)) {
          card.style.display = 'block';
        } else {
          card.style.display = 'none';
        }
      });
    }
    
    function openDoctorModal() {
      document.getElementById('doctorModal').style.display = 'flex';
    }
    
    function closeDoctorModal() {
      document.getElementById('doctorModal').style.display = 'none';
      document.getElementById('doctorForm').reset();
    }
    
    function openBillMaker(doctor) {
      currentDoctor = doctor;
      document.getElementById('premiumPage').style.display = 'none';
      document.getElementById('billMakerSection').style.display = 'block';
      
      // Set doctor name in bill maker
      document.getElementById('doctorName').value = doctor.name;
      document.getElementById('labName').value = document.getElementById('premiumLabName').value;
      
      // Initialize bill maker
      initializeBillMaker();
    }
    
    function goBackToPremiumPage() {
      document.getElementById('billMakerSection').style.display = 'none';
      document.getElementById('premiumPage').style.display = 'block';
    }
    
    // Doctor form submission
    document.getElementById('doctorForm').addEventListener('submit', function(e) {
      e.preventDefault();
      
      const newDoctor = {
        name: document.getElementById('newDoctorName').value,
        clinic: document.getElementById('newClinicName').value,
        phone: document.getElementById('newPhoneNumber').value,
        id: Date.now()
      };
      
      savedDoctors.push(newDoctor);
      localStorage.setItem('savedDoctors', JSON.stringify(savedDoctors));
      
      closeDoctorModal();
      loadDoctors();
    });
    
    // Bill maker original code
    const { jsPDF } = window.jspdf;
    let currentProductCell = null;
    let currentTeethInput = null;
    let currentQtyInput = null;
    let savedBills = JSON.parse(localStorage.getItem('dentalBills')) || [];
    let selectedTeeth = [];

    function initializeBillMaker() {
      const today = new Date();
      document.getElementById('billDate').valueAsDate = today;
      
      // Set current month
      const months = ['January', 'February', 'March', 'April', 'May', 'June', 
                     'July', 'August', 'September', 'October', 'November', 'December'];
      document.getElementById('monthSelect').value = months[today.getMonth()];
      
      // Auto-increment bill number
      if (savedBills.length > 0) {
        const lastBillNo = Math.max(...savedBills.map(bill => parseInt(bill.billNo)));
        document.getElementById('billNo').value = lastBillNo + 1;
      }
      
      // Clear existing rows
      document.getElementById('tableBody').innerHTML = '';
      addRow();
    }

    function addRow() {
      const tbody = document.getElementById('tableBody');
      const row = document.createElement('tr');
      row.innerHTML = `
        <td><input type="date" class="date-info" style="width:100%;" value="${new Date().toISOString().split('T')[0]}"></td>
        <td><input type="text" style="width:100%;"></td>
        <td><button class="product-btn" onclick="openProductSelector(this)">Select</button></td>
        <td><input type="text" style="width:100%;" onclick="openTeethSelector(this)" readonly></td>
        <td><input type="number" style="width:100%; text-align:right;" value="0" oninput="updateRowTotal(this)"></td>
        <td><input type="number" style="width:100%; text-align:right;" value="1" oninput="updateRowTotal(this)"></td>
        <td style="text-align:right;">0.00</td>
      `;
      tbody.appendChild(row);
    }

    function updateRowTotal(input) {
      const row = input.closest('tr');
      const price = parseFloat(row.cells[4].children[0].value) || 0;
      const qty = parseFloat(row.cells[5].children[0].value) || 0;
      row.cells[6].textContent = (price * qty).toFixed(2);
      updateTotals();
    }

    function updateTotals() {
      let subTotal = 0;
      document.querySelectorAll('#tableBody tr').forEach(row => {
        subTotal += parseFloat(row.cells[6].textContent) || 0;
      });
      
      const PREVIOUS = parseFloat(document.getElementById('PREVIOUS').value) || 0;
      const totalBill = subTotal + PREVIOUS;
      const received = parseFloat(document.getElementById('received').value) || 0;
      const balance = totalBill - received;
      
      document.getElementById('subTotal').textContent = subTotal.toFixed(2);
      document.getElementById('totalBill').textContent = totalBill.toFixed(2);
      document.getElementById('balance').textContent = balance.toFixed(2);
    }

    function openProductSelector(button) {
      document.getElementById('productModal').style.display = 'flex';
      currentProductCell = button.parentElement;
    }

    function selectProduct(type) {
      if (currentProductCell) {
        currentProductCell.innerHTML = type;
      }
      closeProductModal();
    }

    function selectCustomProduct() {
      const customText = prompt("Enter custom product:");
      if (customText && currentProductCell) {
        currentProductCell.innerHTML = customText;
      }
      closeProductModal();
    }

    function closeProductModal() {
      document.getElementById('productModal').style.display = 'none';
      currentProductCell = null;
    }

    function openTeethSelector(input) {
      currentTeethInput = input;
      const row = input.closest('tr');
      currentQtyInput = row.cells[5].children[0];
      document.getElementById('teethModal').style.display = 'flex';
      // Clear previous selections
      selectedTeeth = [];
      document.querySelectorAll('#teethSelection .selected').forEach(btn => {
        btn.classList.remove('selected');
      });
    }

    function toggleToothSelection(button) {
      button.classList.toggle('selected');
    }

    function applyTeethSelection() {
      const selectedButtons = document.querySelectorAll('#teethSelection .selected');
      selectedTeeth = Array.from(selectedButtons).map(btn => btn.textContent);
      
      if (currentTeethInput) {
        currentTeethInput.value = selectedTeeth.join(', ');
      }
      if (currentQtyInput) {
        currentQtyInput.value = selectedTeeth.length || 1;
        updateRowTotal(currentQtyInput);
      }
      closeTeethModal();
    }

    function closeTeethModal() {
      document.getElementById('teethModal').style.display = 'none';
      currentTeethInput = null;
    }

    function saveBill() {
      const billData = {
        labName: document.getElementById('labName').value,
        doctorName: document.getElementById('doctorName').value,
        billNo: document.getElementById('billNo').value,
        billDate: document.getElementById('billDate').value,
        month: document.getElementById('monthSelect').value,
        paymentMethod: document.getElementById('paymentMethod').value,
        accountNo1: document.getElementById('accountNo1').value,
        accountNo2: document.getElementById('accountNo2').value,
        items: getTableData(),
        subTotal: document.getElementById('subTotal').textContent,
        PREVIOUS: document.getElementById('PREVIOUS').value,
        totalBill: document.getElementById('totalBill').textContent,
        received: document.getElementById('received').value,
        balance: document.getElementById('balance').textContent,
        timestamp: new Date().toISOString()
      };
      
      savedBills.push(billData);
      localStorage.setItem('dentalBills', JSON.stringify(savedBills));
      
      document.getElementById('savedBillNo').textContent = billData.billNo;
      document.getElementById('savedBillDate').textContent = new Date(billData.billDate).toLocaleDateString();
      document.getElementById('savedTotal').textContent = billData.totalBill;
      document.getElementById('saveSection').style.display = 'block';
    }

    function showSavedBills() {
      const container = document.getElementById('savedBillsContainer');
      const list = document.getElementById('savedBillsList');
      
      list.innerHTML = '';
      
      if (savedBills.length === 0) {
        list.innerHTML = '<p>No saved bills found.</p>';
      } else {
        // Sort by date (newest first)
        const sortedBills = [...savedBills].sort((a, b) => new Date(b.timestamp) - new Date(a.timestamp));
        
        sortedBills.forEach((bill, index) => {
          const billElement = document.createElement('div');
          billElement.style.background = 'white';
          billElement.style.padding = '15px';
          billElement.style.marginBottom = '10px';
          billElement.style.borderRadius = '5px';
          billElement.style.boxShadow = '0 2px 5px rgba(0,0,0,0.1)';
          billElement.innerHTML = `
            <p><strong>Bill #${bill.billNo}</strong> - ${new Date(bill.billDate).toLocaleDateString()}</p>
            <p>Doctor: ${bill.doctorName}</p>
            <p>Total: ${bill.totalBill}</p>
            <button onclick="loadBill(${index})" style="background:#3498db; margin-top:5px;">Load</button>
            <button onclick="deleteBill(${index})" style="background:#e74c3c; margin-top:5px;">Delete</button>
          `;
          list.appendChild(billElement);
        });
      }
      
      container.style.display = 'block';
    }

    function hideSavedBills() {
      document.getElementById('savedBillsContainer').style.display = 'none';
    }

    function loadBill(index) {
      const bill = savedBills[index];
      // Clear current table
      document.getElementById('tableBody').innerHTML = '';
      
      // Set form values
      document.getElementById('labName').value = bill.labName;
      document.getElementById('doctorName').value = bill.doctorName;
      document.getElementById('billNo').value = bill.billNo;
      document.getElementById('billDate').value = bill.billDate;
      document.getElementById('monthSelect').value = bill.month;
      document.getElementById('paymentMethod').value = bill.paymentMethod;
      document.getElementById('accountNo1').value = bill.accountNo1 || '';
      document.getElementById('accountNo2').value = bill.accountNo2 || '';
      document.getElementById('PREVIOUS').value = bill.PREVIOUS;
      document.getElementById('received').value = bill.received;
      
      // Add rows for each item
      bill.items.forEach(item => {
        const row = document.createElement('tr');
        row.innerHTML = `
          <td><input type="date" class="date-info" style="width:100%;" value="${item[0]}"></td>
          <td><input type="text" style="width:100%;" value="${item[1]}"></td>
          <td>${item[2]}</td>
          <td><input type="text" style="width:100%;" value="${item[3]}" onclick="openTeethSelector(this)" readonly></td>
          <td><input type="number" style="width:100%; text-align:right;" value="${item[4]}" oninput="updateRowTotal(this)"></td>
          <td><input type="number" style="width:100%; text-align:right;" value="${item[5]}" oninput="updateRowTotal(this)"></td>
          <td style="text-align:right;">${item[6]}</td>
        `;
        document.getElementById('tableBody').appendChild(row);
      });
      
      // Update totals
      document.getElementById('subTotal').textContent = bill.subTotal;
      document.getElementById('totalBill').textContent = bill.totalBill;
      document.getElementById('balance').textContent = bill.balance;
      
      // Hide saved bills container
      hideSavedBills();
    }

    function deleteBill(index) {
      if (confirm('Are you sure you want to delete this bill?')) {
        savedBills.splice(index, 1);
        localStorage.setItem('dentalBills', JSON.stringify(savedBills));
        showSavedBills(); // Refresh the list
      }
    }

    function resetForm() {
      document.getElementById('tableBody').innerHTML = '';
      document.getElementById('billNo').value = parseInt(document.getElementById('billNo').value) + 1;
      document.getElementById('billDate').valueAsDate = new Date();
      document.getElementById('PREVIOUS').value = 0;
      document.getElementById('received').value = 0;
      document.getElementById('subTotal').textContent = '0.00';
      document.getElementById('totalBill').textContent = '0.00';
      document.getElementById('balance').textContent = '0.00';
      document.getElementById('saveSection').style.display = 'none';
      addRow();
    }

    function generatePDF() {
      const doc = new jsPDF();
      
      // Add transparent curved watermark
      doc.setGState(new doc.GState({opacity: 0.1}));
      doc.setFontSize(40);
      doc.setTextColor(102, 126, 234);
      doc.text('GOOD SMILE DENTAL LAB', 105, 150, { 
        align: 'center',
        angle: -45
      });
      doc.setGState(new doc.GState({opacity: 1}));
      
      // Add border to entire page
      doc.rect(5, 5, doc.internal.pageSize.width - 10, doc.internal.pageSize.height - 10);
      
      // Premium header
      doc.setFontSize(20);
      doc.setTextColor(41, 128, 185);
      doc.setFont(undefined, 'bold');
      doc.text(document.getElementById('labName').value || 'GOOD SMILE DENTAL LAB', 105, 15, { align: 'center' });
      doc.setFontSize(12);
      doc.text('Quality Dental Products', 105, 22, { align: 'center' });
      
      // Bill Info with different colors
      doc.setFontSize(12);
      doc.setTextColor(44, 62, 80); // Dark color for doctor name
      doc.text(`Doctor: ${document.getElementById('doctorName').value}`, 20, 35);
      doc.setTextColor(100, 100, 100); // Normal color for other info
      doc.text(`Bill No: ${document.getElementById('billNo').value}`, 140, 35);
      doc.text(`Date: ${document.getElementById('billDate').value}`, 20, 42);
      doc.text(`Month: ${document.getElementById('monthSelect').value}`, 140, 42);
      
      // Table data
      const headers = [['Date', 'Case No.', 'Product', 'Teeth', 'Price', 'Qty', 'Total']];
      const rows = getTableData();
      
      // Generate table with borders
      doc.autoTable({
        startY: 50,
        head: headers,
        body: rows,
        headStyles: {
          fillColor: [41, 128, 185],
          textColor: 255,
          lineWidth: 0.3,
          fontStyle: 'bold'
        },
        bodyStyles: {
          lineWidth: 0.3,
          lineColor: [100, 100, 100]
        },
        styles: {
          fontSize: 10,
          cellPadding: 4,
          overflow: 'linebreak'
        },
        margin: { top: 50 }
      });
      
      // Summary
      const finalY = doc.lastAutoTable.finalY + 10;
      doc.setFontSize(12);
      doc.text(`SUB-TOTAL: ${document.getElementById('subTotal').textContent}`, 140, finalY);
      doc.text(`PREVIOUS: ${document.getElementById('PREVIOUS').value}`, 140, finalY + 7);
      doc.text(`TOTAL BILL: ${document.getElementById('totalBill').textContent}`, 140, finalY + 14);
      doc.text(`RECEIVED: ${document.getElementById('received').value}`, 140, finalY + 21);
      doc.text(`BALANCE: ${document.getElementById('balance').textContent}`, 140, finalY + 28);
      
      // Payment Info (matching web view font size)
      doc.setFontSize(10);
      doc.text(`Payment Method: ${document.getElementById('paymentMethod').value}`, 20, finalY + 35);
      const accountNo1 = document.getElementById('accountNo1').value;
      const accountNo2 = document.getElementById('accountNo2').value;
      if (accountNo1) doc.text(`Account No 1: ${accountNo1}`, 20, finalY + 42);
      if (accountNo2) doc.text(`Account No 2: ${accountNo2}`, 20, finalY + (accountNo1 ? 49 : 42));
      
      doc.save(`dental_invoice_${document.getElementById('billNo').value}.pdf`);
    }

    function getTableData() {
      const rows = [];
      document.querySelectorAll('#tableBody tr').forEach(row => {
        rows.push([
          row.cells[0].children[0].value,
          row.cells[1].children[0].value,
          row.cells[2].textContent,
          row.cells[3].children[0].value,
          row.cells[4].children[0].value,
          row.cells[5].children[0].value,
          row.cells[6].textContent
        ]);
      });
      return rows;
    }
    
    // Initialize the app
    document.addEventListener('DOMContentLoaded', function() {
      loadDoctors();
    });
  </script>
</body>
</html>
