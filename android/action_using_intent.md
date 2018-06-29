# Examples of action using Intent

## Example

#### Send sms
```java
  Intent smsIntent = new Intent(android.content.Intent.ACTION_VIEW);
  smsIntent.setType("vnd.android-dir/mms-sms");
  smsIntent.putExtra("address","your desired phoneNumber");         
  smsIntent.putExtra("sms_body","your desired message");
  startActivity(smsIntent);
```
#### Phone call
```java
  Intent intent = new Intent(Intent.ACTION_DIAL, Uri.fromParts("tel", "phone_number", null)
  startActivity(intent);
```
#### Open url
```java
  Intent i = new Intent(Intent.ACTION_VIEW);
  i.setData(Uri.parse("URL"));
  startActivity(i);
```
#### Open filemanager/galery
```java
    Intent intent = new Intent(Intent.ACTION_GET_CONTENT);
    intent.setType("FILE_TYPE");//("file/*");("image/*")
    startActivityForResult(intent, YOUR_RESULT_CODE);
 ```
#### Get single contact from phone book
```java
    //start intent
    Intent intent= new Intent(Intent.ACTION_PICK,  Contacts.CONTENT_URI);
    startActivityForResult(intent, PICK_CONTACT);
        
    @Override
    public void onActivityResult(int reqCode, int resultCode, Intent data) {
      super.onActivityResult(reqCode, resultCode, data);
      //get data from choosen contact
      switch (reqCode) {
        case (PICK_CONTACT) :
          if (resultCode == Activity.RESULT_OK) {
            Uri contactData = data.getData();
            Cursor c =  managedQuery(contactData, null, null, null, null);
            if (c.moveToFirst()) {
              String name = c.getString(c.getColumnIndex(ContactsContract.Contacts.DISPLAY_NAME));
              // TODO Fetch other Contact details as you want to use

            }
          }
          break;
      }
    }
 ```