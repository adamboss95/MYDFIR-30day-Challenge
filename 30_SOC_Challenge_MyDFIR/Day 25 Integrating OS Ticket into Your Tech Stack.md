# Day 25: Integrating OS Ticket into Your Tech Stack

## 1. Introduction

**Goal**: Successfully integrate OS Ticket into your tech stack and confirm the integration by sending a test alert.

## 2. Setting Up API Key in OS Ticket

**Steps**:

**Access OS Ticket Admin Panel**:

- Click on `Admin` at the top right corner.
- Select `Manage` and then `API`.

**Add New API Key**:
   
- Click on ~Add New API Key~.
- Enter the private IP address of your `MyDFIR-ELK` server (if in the same VPC) or the public IP address (if not).
- Enable the `Can Create Tickets` service.
- Add internal notes (e.g., `MyDFIR- 30 day SOC  Elastic Connector`).
- Click `Add Key` and copy the generated API key.

## 3. Configuring Elastic Connector

**Steps**:

**Enable Free 30-Day Trial**:
   
- Go to `Stack Management` under the hamburger icon.
- Select `Manage License` and start the 30-day trial.

**Create Connector**:

- Go to `Connectors` under `Alerts and Insights`.
- Click on `Create Connector`
- Choose `Web Hook` and name it `OS Ticket`.
- Set the request type to `POST`
- Enter the URL: `http://<OS_Ticket_IP>/osticket/upload/api/tickets.xml`
- Select `None` for authentication
- Add an HTTP header with the key `x-api-key` and the value as the copied API key.
- Click `Save and Test`.

## 4. Creating Action Body

**Steps**:

**Get XML Payload Example**:
 
- Go to OS Ticket's GitHub page for ticket creation examples.
- Copy the XML payload example.

```
<?xml version="1.0" encoding="UTF-8"?>
<ticket alert="true" autorespond="true" source="API">
    <name>Angry User</name>
    <email>api@osticket.com</email>
    <subject>MyDFIR-30DayChallenge-Wahab</subject>
    <phone>318-555-8634X123</phone>
    <message type="text/plain"><![CDATA[Message content here]]></message>
    <attachments>
        <file name="file.txt" type="text/plain"><![CDATA[
            File content is here and is automatically trimmed
        ]]></file>
        <file name="image.gif" type="image/gif" encoding="base64">
            R0lGODdhMAAwAPAAAAAAAP///ywAAAAAMAAwAAAC8IyPqcvt3wCcDkiLc7C0qwy
            GHhSWpjQu5yqmCYsapyuvUUlvONmOZtfzgFzByTB10QgxOR0TqBQejhRNzOfkVJ
            +5YiUqrXF5Y5lKh/DeuNcP5yLWGsEbtLiOSpa/TPg7JpJHxyendzWTBfX0cxOnK
            PjgBzi4diinWGdkF8kjdfnycQZXZeYGejmJlZeGl9i2icVqaNVailT6F5iJ90m6
            mvuTS4OK05M0vDk0Q4XUtwvKOzrcd3iq9uisF81M1OIcR7lEewwcLp7tuNNkM3u
            Nna3F2JQFo97Vriy/Xl4/f1cf5VWzXyym7PHhhx4dbgYKAAA7
        </file>
    </attachments>
    <ip>123.211.233.122</ip>
</ticket>
```

**Customize Payload**:
 
- Paste the XML payload into the connector action body.
- Change the subject to `Callenge - Wahab`.

## 5. Troubleshooting Connection Issues

**Steps**:

1. **Check Network Connection**:
    
    - If you encounter a timeout error, it indicates a network connection issue.
    - Open a PowerShell session and `SSH` into your `MyDFIR-ELK` server to troubleshoot.

2. **Verify IP Configuration**:
    
    - Ensure the OS Ticket server has the correct private IP address.
    - Update the network adapter settings if necessary to set IPv4 address to the MyDFIR-OSticket Private VPC address.

3. **Update Connector Configuration**:
    
    - Change the connector URL to use the private `MyDFIR-OSticket ` server IP address of the OS Ticket server.
    - Save and rerun the test.

## 6. Confirming Integration

**Steps**:

1. **Check OS Ticket**:
    
    - Go to the agent panel in OS Ticket.
    - Verify that the test alert has created a ticket.

2. **Review Ticket**:
    
    - Ensure the ticket details match the expected results.

## 7. Conclusion

**Summary**:

- Successfully integrated OS Ticket into your tech stack.
- Confirmed the integration by sending a test alert and creating a ticket.