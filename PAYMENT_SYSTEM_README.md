# SOMUN 2025 Payment Tracking System

## Overview
The registration form now includes an automated payment tracking system that generates unique QR codes for each registration with embedded payment reference codes.

## How It Works

### For Students/Registrants:
1. **Unique Code Generation**: Each registration form generates a unique payment code in format `SOMUN25-XXXXXX`
2. **Dynamic QR Code**: A UPI QR code is automatically generated containing:
   - UPI ID: `skl@upi`
   - Amount: ₹2700
   - Payment Description: The unique payment code
3. **Easy Reference**: The payment code is displayed prominently with a copy button
4. **Screenshot Upload**: Students still upload transaction screenshots as backup verification

### For Administrators:
1. **Payment Verification Process**:
   - Check UPI transaction statements for payments of ₹2700
   - Match the payment description in statements with the `payment_code` column in your Excel registration data
   - Cross-reference with uploaded screenshots if needed

2. **Data Structure**: Each registration submission now includes:
   - All existing registration data
   - `payment_code`: Unique identifier for payment tracking
   - `screenshot`: Base64 encoded transaction screenshot

## Technical Implementation

### Code Structure:
- **Payment Code Generation**: `generatePaymentCode()` - Creates unique codes using timestamp + random string
- **QR Code Generation**: `generateUPIQRCode()` - Creates UPI payment QR codes with embedded payment descriptions
- **UI Updates**: Dynamic QR display, payment code highlighting, copy functionality
- **Form Integration**: Payment codes are included in form submission data

### Libraries Used:
- QRCode.js: For generating QR codes
- Native Web APIs: For clipboard functionality

## Benefits

1. **Automated Tracking**: No manual effort needed to generate unique codes
2. **Easy Verification**: Direct matching between UPI statements and registration data
3. **Reduced Errors**: Eliminates manual payment matching errors
4. **Professional Appearance**: Clean, modern payment interface
5. **Backup Verification**: Screenshots provide additional verification layer

## Payment Verification Workflow

1. **Student Side**:
   - Scan QR code with any UPI app
   - Payment description automatically includes unique code
   - Upload transaction screenshot
   - Submit registration

2. **Admin Side**:
   - Export registration data from Google Sheets
   - Check UPI account statement
   - Match payment descriptions with `payment_code` column
   - Mark payments as verified in Excel sheet

This system ensures accurate, automated payment tracking while maintaining user-friendly registration experience.