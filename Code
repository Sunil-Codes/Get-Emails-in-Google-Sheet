function getEmails() {
  var ss = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Email Data');
  var today = new Date();
  var todate = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Last run time').getRange('a1').getValue();
  var dd = today.getDate() - 1;
  var mm = today.getMonth() + 1; //January is 0 DO NOT FORGET THIS
  var yyyy = today.getFullYear();
  var yesterday = yyyy + '/' + mm + '/' + dd;

  var query = "in:inbox  after:" + yesterday;
  var thread = GmailApp.search(query)   //puting query in gmail to search emails



  for (var i = thread.length - 1; i >= 0; i--) {

    var message = thread[i].getMessages();

    for (var j = 0; j < message.length; j++) {
      Logger.log(message.length)

      var support = [];  // will fill the data in this and apend in row


      var from = message[j].getFrom();
      var time = message[j].getDate();
      var sub = message[j].getSubject();
      var body = message[j].getPlainBody();
      var url = message[j].getId();


      var mYear = time.getFullYear();
      var mMonth = time.getMonth() + 1;
      var mDay = time.getDate();
      var messageDate = mYear + '/' + mMonth + '/' + mDay;
      // Logger.log(time+"and"+todate)
      // Logger.log(time>todate)
      if (time > todate) {
        support.push(from);
        support.push(time);
        support.push(sub);
        support.push(body);
        support.push('https://mail.google.com/mail/u/0/#inbox/' + url);

        ss.appendRow(support)

      }



    }


  }
}
