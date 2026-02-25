# talentregister
add talent
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SPLD & CPLI - Data Entry Form</title>
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
:root {
  --primary: #1F4E78;
  --primary-light: #2B6CB0;
  --accent: #ED8936;
  --bg: #F7FAFC;
  --card: #FFFFFF;
  --text: #2D3748;
  --text-light: #718096;
  --border: #E2E8F0;
  --success: #48BB78;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, var(--primary), var(--primary-light));
  min-height: 100vh;
  padding: 20px;
  color: var(--text);
}

.container {
  max-width: 900px;
  margin: 0 auto;
  background: var(--card);
  border-radius: 16px;
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
  overflow: hidden;
}

.header {
  background: linear-gradient(135deg, var(--primary), var(--primary-light));
  color: white;
  padding: 32px;
  text-align: center;
}

.header h1 {
  font-size: 28px;
  margin-bottom: 8px;
  font-weight: 700;
}

.header p {
  font-size: 14px;
  opacity: 0.9;
}

.form-section {
  padding: 32px;
}

.form-group {
  margin-bottom: 24px;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 20px;
}

.form-row.full {
  grid-template-columns: 1fr;
}

@media (max-width: 600px) {
  .form-row { grid-template-columns: 1fr; }
}

label {
  display: block;
  font-weight: 600;
  margin-bottom: 8px;
  color: var(--primary);
  font-size: 14px;
}

.required {
  color: #E53E3E;
  margin-left: 4px;
}

input, select, textarea {
  width: 100%;
  padding: 12px 14px;
  border: 2px solid var(--border);
  border-radius: 8px;
  font-size: 14px;
  font-family: inherit;
  transition: border 0.2s;
}

input:focus, select:focus, textarea:focus {
  outline: none;
  border-color: var(--primary-light);
  box-shadow: 0 0 0 3px rgba(43, 108, 176, 0.1);
}

textarea {
  resize: vertical;
  min-height: 80px;
}

.btn-group {
  display: flex;
  gap: 12px;
  margin-top: 32px;
  flex-wrap: wrap;
}

.btn {
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  flex: 1;
  min-width: 120px;
}

.btn-submit {
  background: var(--primary);
  color: white;
}

.btn-submit:hover {
  background: var(--primary-light);
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(31, 78, 120, 0.3);
}

.btn-reset {
  background: var(--border);
  color: var(--text);
}

.btn-reset:hover {
  background: #CBD5E0;
}

.btn-download {
  background: var(--success);
  color: white;
}

.btn-download:hover {
  background: #38A169;
}

.success-message {
  display: none;
  background: #C6F6D5;
  border-left: 4px solid var(--success);
  color: #22543D;
  padding: 16px;
  border-radius: 8px;
  margin-bottom: 20px;
  animation: slideIn 0.3s ease;
}

.success-message.show {
  display: flex;
  align-items: center;
  gap: 12px;
}

@keyframes slideIn {
  from { transform: translateY(-20px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

.data-table {
  margin-top: 32px;
  overflow-x: auto;
}

.data-table table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}

.data-table th {
  background: var(--primary);
  color: white;
  padding: 12px;
  text-align: left;
  font-weight: 600;
}

.data-table td {
  padding: 10px 12px;
  border-bottom: 1px solid var(--border);
}

.data-table tr:hover {
  background: var(--bg);
}

.data-table .btn-delete {
  background: #FED7D7;
  color: #9B2C2C;
  padding: 4px 8px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 12px;
}

.data-table .btn-delete:hover {
  background: #FC8181;
}

.tabs {
  display: flex;
  border-bottom: 2px solid var(--border);
  margin-bottom: 20px;
}

.tab {
  padding: 12px 20px;
  background: none;
  border: none;
  cursor: pointer;
  font-weight: 600;
  color: var(--text-light);
  border-bottom: 3px solid transparent;
  transition: all 0.2s;
}

.tab.active {
  color: var(--primary);
  border-bottom-color: var(--primary);
}

.tab:hover {
  color: var(--primary);
}

.tab-content {
  display: none;
}

.tab-content.active {
  display: block;
}

.empty-state {
  text-align: center;
  padding: 40px 20px;
  color: var(--text-light);
}

.empty-state svg {
  width: 48px;
  height: 48px;
  margin-bottom: 16px;
  opacity: 0.4;
}

.stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin-bottom: 20px;
}

.stat-box {
  background: var(--bg);
  padding: 16px;
  border-radius: 8px;
  text-align: center;
  border-left: 4px solid var(--primary);
}

.stat-box .num {
  font-size: 24px;
  font-weight: 700;
  color: var(--primary);
}

.stat-box .label {
  font-size: 12px;
  color: var(--text-light);
  margin-top: 4px;
}

@media (max-width: 600px) {
  .header { padding: 20px; }
  .form-section { padding: 20px; }
  .stats { grid-template-columns: 1fr; }
  .header h1 { font-size: 22px; }
}
</style>
</head>
<body>

<div class="container">
  <div class="header">
    <h1>📋 SPLD & CPLI Data Entry Form</h1>
    <p>ระบบป้อนข้อมูลพนักงาน | Employee Data Management System</p>
  </div>

  <div class="form-section">
    <div class="success-message" id="successMsg">
      ✅ <span id="successText">บันทึกข้อมูลสำเร็จ</span>
    </div>

    <div class="tabs">
      <button class="tab active" onclick="switchTab(0)">📝 ป้อนข้อมูล</button>
      <button class="tab" onclick="switchTab(1)">📊 ข้อมูลทั้งหมด</button>
      <button class="tab" onclick="switchTab(2)">📥 จัดการไฟล์</button>
    </div>

    <!-- Tab 1: Form Entry -->
    <div class="tab-content active" id="tab-0">
      <form id="dataForm" onsubmit="submitForm(event)">
        <div class="form-row">
          <div class="form-group">
            <label>รหัสพนักงาน <span class="required">*</span></label>
            <input type="text" id="empId" required placeholder="e.g., 01234567">
          </div>
          <div class="form-group">
            <label>ชื่อ <span class="required">*</span></label>
            <input type="text" id="firstName" required placeholder="First Name">
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label>นามสกุล <span class="required">*</span></label>
            <input type="text" id="lastName" required placeholder="Last Name">
          </div>
          <div class="form-group">
            <label>ปี <span class="required">*</span></label>
            <input type="number" id="year" required min="2016" max="2030" placeholder="2025">
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label>Group</label>
            <select id="group">
              <option value="">-- เลือก --</option><option value="CPLI">CPLI</option><option value="SPLD">SPLD</option><option value="CPG-SPLD">CPG-SPLD</option>
            </select>
          </div>
          <div class="form-group">
            <label>Sub Group</label>
            <select id="subGroup">
              <option value="">-- เลือก --</option><option value="LDP">LDP</option><option value="CEXI">CEXI</option><option value="SPTM">SPTM</option><option value="FLP">FLP</option><option value="CSO">CSO</option><option value="Network">Network</option><option value="Strategic">Strategic</option><option value="Micro">Micro</option><option value="Imperative">Imperative</option><option value="O2O">O2O</option><option value="FBL">FBL</option><option value="SLP">SLP</option><option value="PLP">PLP</option><option value="CLM">CLM</option><option value="True Ryde">True Ryde</option><option value="Top University">Top University</option><option value="ALP">ALP</option><option value="BLP">BLP</option><option value="NLP">NLP</option>
            </select>
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label>Program</label>
            <select id="program">
              <option value="">-- เลือก --</option><option value="LDP2">LDP2</option><option value="CEXI Ph 1">CEXI Ph 1</option><option value="CEXI Ph 2">CEXI Ph 2</option><option value="CEXI Ph 3">CEXI Ph 3</option><option value="SPTM">SPTM</option><option value="FLP1">FLP1</option><option value="FLP2">FLP2</option><option value="CSO3">CSO3</option><option value="CSO4">CSO4</option><option value="CSOx">CSOx</option><option value="True Captain">True Captain</option><option value="Commercial">Commercial</option><option value="O2O Ph 1">O2O Ph 1</option><option value="O2O Ph 2">O2O Ph 2</option><option value="LDP-True">LDP-True</option><option value="FBL1">FBL1</option><option value="I-Sarn">I-Sarn</option><option value="Network Modular">Network Modular</option><option value="Digitization">Digitization</option><option value="Corporate Strategy">Corporate Strategy</option>
            </select>
          </div>
          <div class="form-group">
            <label>Role</label>
            <select id="role">
              <option value="">-- เลือก --</option><option value="Member">Member</option><option value="Leader">Leader</option><option value="Sponsor">Sponsor</option><option value="Coach">Coach</option><option value="Support">Support</option><option value="Group Sponsor">Group Sponsor</option><option value="Mini Sponsor">Mini Sponsor</option><option value="Strategy Sponsor">Strategy Sponsor</option><option value="Project Owner">Project Owner</option><option value="Project Sponsor">Project Sponsor</option><option value="Champion">Champion</option><option value="Mentor">Mentor</option><option value="Principal">Principal</option>
            </select>
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label>Performance</label>
            <select id="performance">
              <option value="">-- เลือก --</option><option value="H">H</option><option value="M">M</option><option value="L">L</option><option value="Pass">Pass</option><option value="Not Pass">Not Pass</option>
            </select>
          </div>
          <div class="form-group">
            <label>Action</label>
            <select id="action">
              <option value="">-- เลือก --</option>
              <option value="New">New</option>
              <option value="Update">Update</option>
              <option value="Delete">Delete</option>
            </select>
          </div>
        </div>

        <div class="form-row full">
          <div class="form-group">
            <label>หมายเหตุ (Remark)</label>
            <textarea id="remark" placeholder="เพิ่มหมายเหตุหรือข้อมูลเพิ่มเติม..."></textarea>
          </div>
        </div>

        <div class="btn-group">
          <button type="submit" class="btn btn-submit">💾 บันทึกข้อมูล</button>
          <button type="reset" class="btn btn-reset">🔄 ล้างข้อมูล</button>
        </div>
      </form>
    </div>

    <!-- Tab 2: Data View -->
    <div class="tab-content" id="tab-1">
      <div class="stats">
        <div class="stat-box">
          <div class="num" id="statCount">0</div>
          <div class="label">รายการทั้งหมด</div>
        </div>
        <div class="stat-box">
          <div class="num" id="statToday">0</div>
          <div class="label">เพิ่มวันนี้</div>
        </div>
        <div class="stat-box">
          <div class="num" id="statGroups">0</div>
          <div class="label">Group ที่มี</div>
        </div>
      </div>

      <div class="data-table" id="dataTableContainer">
        <div class="empty-state">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm.5-13H11v6l5.2 3.2.8-1.3-4.5-2.7V7z"/>
          </svg>
          <h3>ยังไม่มีข้อมูล</h3>
          <p>ป้อนข้อมูลจากแท็บ "ป้อนข้อมูล"</p>
        </div>
      </div>
    </div>

    <!-- Tab 3: File Management -->
    <div class="tab-content" id="tab-2">
      <div class="form-group">
        <h3 style="margin-bottom: 16px; color: var(--primary);">📥 จัดการไฟล์</h3>
        <p style="color: var(--text-light); margin-bottom: 16px;">
          ดาวน์โหลดข้อมูลเป็นไฟล์ Excel หรือ CSV เพื่อนำไปใช้งานต่อ
        </p>
        <div class="btn-group">
          <button class="btn btn-download" onclick="downloadExcel()">📊 Download Excel</button>
          <button class="btn btn-download" onclick="downloadCSV()">📋 Download CSV</button>
          <button class="btn btn-reset" onclick="clearAllData()">🗑️ ลบข้อมูลทั้งหมด</button>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
const STORAGE_KEY = 'spldCpliData';

function switchTab(index) {
  const tabs = document.querySelectorAll('.tab');
  const contents = document.querySelectorAll('.tab-content');
  tabs.forEach((t, i) => t.classList.toggle('active', i === index));
  contents.forEach((c, i) => c.classList.toggle('active', i === index));
  if (index === 1) renderTable();
}

function getStoredData() {
  const data = localStorage.getItem(STORAGE_KEY);
  return data ? JSON.parse(data) : [];
}

function saveData(records) {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(records));
}

function submitForm(e) {
  e.preventDefault();
  const record = {
    id: Date.now(),
    empId: document.getElementById('empId').value,
    firstName: document.getElementById('firstName').value,
    lastName: document.getElementById('lastName').value,
    year: document.getElementById('year').value,
    group: document.getElementById('group').value,
    subGroup: document.getElementById('subGroup').value,
    program: document.getElementById('program').value,
    role: document.getElementById('role').value,
    performance: document.getElementById('performance').value,
    action: document.getElementById('action').value,
    remark: document.getElementById('remark').value,
    timestamp: new Date().toLocaleString('th-TH')
  };

  let records = getStoredData();
  records.push(record);
  saveData(records);

  document.getElementById('dataForm').reset();
  showSuccess(`บันทึก ${record.firstName} ${record.lastName} สำเร็จ`);
  updateStats();
}

function showSuccess(msg) {
  const el = document.getElementById('successMsg');
  document.getElementById('successText').textContent = msg;
  el.classList.add('show');
  setTimeout(() => el.classList.remove('show'), 3000);
}

function renderTable() {
  const records = getStoredData();
  if (!records.length) return;
  
  let html = '<table><tr><th>ลำดับ</th><th>รหัสพนักงาน</th><th>ชื่อ</th><th>ปี</th><th>Group</th><th>Program</th><th>Action</th><th>วันที่</th><th></th></tr>';
  records.forEach((r, i) => {
    html += `<tr>
      <td>${i+1}</td>
      <td>${r.empId}</td>
      <td>${r.firstName} ${r.lastName}</td>
      <td>${r.year}</td>
      <td>${r.group}</td>
      <td>${r.program}</td>
      <td>${r.action}</td>
      <td style="font-size:11px;color:var(--text-light)">${r.timestamp}</td>
      <td><button class="btn-delete" onclick="deleteRecord(${r.id})">ลบ</button></td>
    </tr>`;
  });
  html += '</table>';
  document.getElementById('dataTableContainer').innerHTML = html;
}

function deleteRecord(id) {
  if (!confirm('ยืนยันการลบ?')) return;
  let records = getStoredData();
  records = records.filter(r => r.id !== id);
  saveData(records);
  renderTable();
  updateStats();
}

function updateStats() {
  const records = getStoredData();
  const today = new Date().toLocaleDateString('th-TH');
  document.getElementById('statCount').textContent = records.length;
  document.getElementById('statToday').textContent = records.filter(r => r.timestamp.includes(today.split('/')[0])).length;
  document.getElementById('statGroups').textContent = new Set(records.map(r => r.group).filter(Boolean)).size;
}

function downloadExcel() {
  const records = getStoredData();
  if (!records.length) { alert('ไม่มีข้อมูล'); return; }
  
  let csv = 'รหัสพนักงาน,ชื่อ,นามสกุล,ปี,Group,Sub Group,Program,Role,Performance,Action,หมายเหตุ,วันที่\n';
  records.forEach(r => {
    csv += `"${r.empId}","${r.firstName}","${r.lastName}",${r.year},"${r.group}","${r.subGroup}","${r.program}","${r.role}","${r.performance}","${r.action}","${r.remark}","${r.timestamp}"\n`;
  });
  
  const blob = new Blob([csv], {type: 'text/csv;charset=utf-8;'});
  const link = document.createElement('a');
  link.href = URL.createObjectURL(blob);
  link.download = 'SPLD_CPLI_Data_' + new Date().toISOString().split('T')[0] + '.csv';
  link.click();
  showSuccess('ดาวน์โหลดสำเร็จ');
}

function downloadCSV() {
  downloadExcel();
}

function clearAllData() {
  if (!confirm('ยืนยันการลบข้อมูลทั้งหมด?')) return;
  localStorage.removeItem(STORAGE_KEY);
  updateStats();
  document.getElementById('dataTableContainer').innerHTML = '<div class="empty-state"><p>ข้อมูลถูกลบแล้ว</p></div>';
  showSuccess('ลบข้อมูลทั้งหมดแล้ว');
}

// Init
updateStats();
</script>
</body>
</html>
