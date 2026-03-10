// @ts-nocheck
// Developed by Achmad Sabiqun Nugraha
// Monitoring Kontrol Pemakaian Tools - Fixed Google Drive Access
// MASUKKAN ID FOLDER ANDA DI SINI
const FOLDER_ID = "1B4bBiJ8Evfgk5QrOZ7orRLnqAeqhDNxi";
function setupDatabase() {
const ss = SpreadsheetApp.getActiveSpreadsheet();
// 1. Sheet Settings
let sheetSettings = ss.getSheetByName('Settings');
if (!sheetSettings) {
sheetSettings = ss.insertSheet('Settings');
sheetSettings.appendRow(['Parameter', 'Value', 'Keterangan']);
}
// Update Folder ID secara otomatis ke sheet Settings
const settingsData = sheetSettings.getDataRange().getValues();
let found = false;
for (let i = 0; i < settingsData.length; i++) {
if (settingsData[i][0] === 'Drive_Folder_ID') {
sheetSettings.getRange(i + 1, 2).setValue(FOLDER_ID);
found = true;
break;
}
}
if (!found) {
sheetSettings.appendRow(['Drive_Folder_ID', FOLDER_ID, 'ID Folder Drive untuk simpan Foto']);
}
// 2. Sheet Data Tool
let sheetEmp = ss.getSheetByName('Data Tool/ Insert');
if (!sheetEmp) {
sheetEmp = ss.insertSheet('Data Tool/ Insert');
sheetEmp.appendRow(['Nama Tool/ Insert']);
}
// 3. Sheet Transaksi
let sheetAtt = ss.getSheetByName('Data Kontrol Pemakaian Tools');
if (!sheetAtt) {
sheetAtt = ss.insertSheet('Data Kontrol Pemakaian Tools');
}
sheetAtt.getRange(1, 1, 1, 8).setValues([[
'Tanggal', 'Nama Tool/ Insert', 'QTY', 'Produk', 'Mesin', 'PIC', 'Keterangan', 'Link Foto'
]]);
return "Setup Berhasil! Folder ID telah dikonfigurasi ke: " + FOLDER_ID;
}
function doGet() {
return HtmlService.createTemplateFromFile('index')
.evaluate()
.setTitle('Monitoring Kontrol Penggunaan Tools')
.addMetaTag('viewport', 'width=device-width, initial-scale=1')
.setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}
function getInitialData() {
const ss = SpreadsheetApp.getActiveSpreadsheet();
const settingsSheet = ss.getSheetByName('Settings');
const empSheet = ss.getSheetByName('Data Tool/ Insert');
const attSheet = ss.getSheetByName('Data Kontrol Pemakaian Tools');
const employees = empSheet.getLastRow() > 1
? empSheet.getRange(2, 1, empSheet.getLastRow() - 1, 1).getValues().flat().filter(String)
: [];
const lastRow = attSheet.getLastRow();
const history = lastRow > 1
? attSheet.getRange(Math.max(2, lastRow - 19), 1, Math.min(20, lastRow - 1), attSheet.getLastColumn()).getDisplayValues().reverse()
: [];
return JSON.stringify({ employees, history });
}
function submitAttendance(payload) {
try {
const data = JSON.parse(payload);
const ss = SpreadsheetApp.getActiveSpreadsheet();
const attSheet = ss.getSheetByName('Data Kontrol Pemakaian Tools');
code
Code
// UPLOAD FOTO KE GOOGLE DRIVE
let fileUrl = "No Photo";
if (data.image && data.image.startsWith('data:image')) {
  try {
    // Menggunakan FOLDER_ID yang sudah didefinisikan di atas
    const folder = DriveApp.getFolderById(FOLDER_ID);
    
    const contentType = data.image.substring(5, data.image.indexOf(';'));
    const bytes = Utilities.base64Decode(data.image.split(',')[1]);
    const fileName = "Tool_" + data.name + "_" + Utilities.formatDate(new Date(), "GMT+7", "yyyyMMdd_HHmm") + ".jpg";
    
    const blob = Utilities.newBlob(bytes, contentType, fileName);
    const file = folder.createFile(blob);
    
    // Memastikan file bisa diakses publik (agar link foto bisa diklik di sheet)
    file.setSharing(DriveApp.Access.ANYONE_WITH_LINK, DriveApp.Permission.VIEW);
    fileUrl = file.getUrl();
  } catch (err) {
    fileUrl = "Gagal Upload: " + err.toString();
  }
}

// SIMPAN KE GOOGLE SHEET
attSheet.appendRow([
  new Date(),
  data.name,
  data.qty,
  data.product,
  data.machine,
  data.pic,
  data.desc,
  fileUrl
]);

return JSON.stringify({ success: true, message: "Data dan Foto berhasil disimpan!" });
} catch (e) {
return JSON.stringify({ success: false, message: "Error: " + e.toString() });
}
}

    // === UPLOAD FOTO ===
    let fileId = "No Image";
    if (data.image && data.image.startsWith('data:image')) {
      try {
        const folderId = settings['Drive_Folder_ID'];
        const folder = folderId && folderId.toString().trim() 
          ? DriveApp.getFolderById(folderId) 
          : DriveApp.getRootFolder();
        
        const contentType = data.image.substring(5, data.image.indexOf(';'));
        const bytes = Utilities.base64Decode(data.image.split(',')[1]);
        const blob = Utilities.newBlob(bytes, contentType, `Absen_${safeName}_${safeShift}_${Date.now()}.jpg`);
        const file = folder.createFile(blob);
        file.setSharing(DriveApp.Access.ANYONE_WITH_LINK, DriveApp.Permission.VIEW);
        fileId = file.getId();
      } catch(e) {
        console.error("Upload error:", e);
        fileId = "Error Upload";
      }
    }

    // === HITUNG STATUS (Tepat Waktu / Terlambat) ===
    const isLate = jakartaTime.getTime() > shiftDate.getTime();
    const status = isLate ? "Terlambat" : "Tepat Waktu";
    
    let diffText = "Absensi Tepat Waktu";
    if (isLate) {
      const diffMs = jakartaTime.getTime() - shiftDate.getTime();
      const diffHrs = Math.floor(diffMs / 3600000);
      const diffMins = Math.round((diffMs % 3600000) / 60000);
      diffText = diffHrs > 0 ? `Terlambat ${diffHrs} jam ${diffMins} menit` : `Terlambat ${diffMins} menit`;
    }

    // === SIMPAN KE SPREADSHEET ===
    attSheet.appendRow([
      new Date(), // Timestamp server
      safeName,
      safeShift,
      status,
      data.distance || 0,
      `${data.lat || 0},${data.lng || 0}`,
      fileId,
      diffText
    ]);

    return JSON.stringify({
      success: true,
      status: status,
      message: isLate 
        ? `${diffText}. Tetap semangat, usahakan besok lebih awal!` 
        : `Luar biasa, Anda tepat waktu! Terima kasih atas dedikasinya.`
    });
    
  } catch (e) {
    console.error("Submit error:", e);
    return JSON.stringify({
      success: false,
      message: "Terjadi kesalahan sistem. Silakan coba lagi atau hubungi admin."
    });
  }
}

/**
 * Helper: Hitung jarak koordinat (Haversine formula)
 */
function calculateDistance(lat1, lon1, lat2, lon2) {
  const R = 6371e3;
  const dLat = (lat2 - lat1) * Math.PI / 180;
  const dLon = (lon2 - lon1) * Math.PI / 180;
  const a = Math.sin(dLat/2) * Math.sin(dLat/2) + 
            Math.cos(lat1 * Math.PI/180) * Math.cos(lat2 * Math.PI/180) * 
            Math.sin(dLon/2) * Math.sin(dLon/2);
  return Math.round(R * 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a)));
}
