# MS Graph API Mailer - Test Functionality

## New Features Added

### 1. Check Permissions Button
- **Purpose**: Verify that the Azure AD connection is working and Mail.Send permission is enabled
- **Location**: Settings page → Test Configuration section
- **How it works**: 
  - Tests connection to Microsoft Graph API
  - Verifies OAuth2 token can be obtained
  - Confirms Mail.Send permission is granted

### 2. Send Test Email Button
- **Purpose**: Send a test email to verify the complete email sending flow
- **Location**: Settings page → Test Configuration section
- **How it works**:
  - Takes a test email address from the input field
  - Sends a test email via Microsoft Graph API
  - Shows success or failure message

## Usage

### Step 1: Configure Azure Settings
1. Go to: Site Administration → Plugins → Local plugins → MS Graph API Mailer
2. Enter your Azure AD credentials:
   - Tenant ID
   - Client ID
   - Client Secret
   - Sender Email (must exist in your Microsoft 365)
3. Save changes

### Step 2: Test Permissions
1. Click **"Check Permissions"** button
2. Expected result: ✓ Connection successful! Mail.Send permission is enabled.
3. If failed: Check your credentials and Azure AD permissions

### Step 3: Test Email Sending
1. Enter a test email address in the "Test Email Address" field
2. Click **"Send Test Email"** button
3. Expected result: ✓ Test email sent successfully!
4. Check the recipient's inbox for the test email

## Files Added/Modified

### New Files
- `ajax.php` - AJAX handler for test functionality
- `amd/src/tester.js` - JavaScript for test buttons
- `amd/build/tester.min.js` - Minified JavaScript
- `TEST_FUNCTIONALITY.md` - This documentation

### Modified Files
- `settings.php` - Added test configuration section
- `lang/en/local_msgraph_mailer.php` - Added test-related language strings

## API Endpoints

### Check Permissions
```
POST /local/msgraph_mailer/ajax.php
Data: action=check_permissions
```

### Send Test Email
```
POST /local/msgraph_mailer/ajax.php
Data: action=send_test_email&email=user@example.com
```

## Troubleshooting

### "Permission check failed"
- Verify Tenant ID, Client ID, and Client Secret are correct
- Check that Mail.Send permission is granted in Azure AD
- Ensure admin consent is granted

### "Email sent failed"
- Verify Sender Email exists in Microsoft 365
- Check Azure AD has proper licensing
- Verify SMTP/Exchange limits haven't been exceeded
