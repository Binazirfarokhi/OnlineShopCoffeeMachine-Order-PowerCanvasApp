# OnlineShopCoffeeMachine
## Machine Ordering App (Power Apps + Dataverse + Power Automate)

This app is an **online machine/coffee equipment ordering system** built in Microsoft Power Platform. Instead of sending emails or using a manual form, users can browse machines, view details, submit an order, and automatically get an email confirmation.

---

### What the app does

- ✅ Shows a catalog of coffee/machine products with images and prices
- ✅ Lets the user **select a machine** to order
- ✅ Captures order details (price, approver email, comments/justification, requested by)
- ✅ Saves the order in **Dataverse** (`Machine order` table)
- ✅ Triggers a **Power Automate** flow to send an email to the requester with the order details

---

### Demo

**Browse & select a machine**

![Machine selection](SelectMachine.gif)

**Submit an order and send email**

![Order machine flow](orderMachine.gif)

> 💡 Update the GIF paths above if you store them in `/assets/`:
> ```markdown
> ![Machine selection](assets/SelectMachine.gif)
> ![Order machine flow](assets/orderMachine.gif)
> ```

---

### Components

- **Canvas App**: `Machine Ordering App`
  - UI to browse machines
  - Form to submit the order
- **Dataverse table**: `Machine order`
  - Stores the order record (machine, price, requester, comments, etc.)
- **Power Automate flow**: `SendMachineOrderEmail`
  - Trigger: **When Power Apps calls a flow (V2)**
  - Action: **Send an email (V2)**
  - Email includes dynamic values: **Name**, **Guests / quantity**, **ItemJson / machine details**

---

### Technology used

- Microsoft **Power Apps (Canvas App)**
- **Dataverse** for data storage
- **Power Automate** for email notification
- Model based on **Contoso** sample catalog UI

---

### How it works (flow)

1. User selects a machine in the Canvas App.
2. User fills in details (price, approver, comments, requested by).
3. App creates a record in the **Machine order** Dataverse table.
4. App calls the **SendMachineOrderEmail** cloud flow and passes parameters.
5. Flow sends an email like:  
   > “Hello \<Name\>, here are your order details: \<Item\> …”

---

### Business value

- Replaces manual/phone/email requests
- Standardizes order data in Dataverse
- Notifies the requester immediately
- Can be extended to approvals later (e.g. Approver must approve before order is active)
