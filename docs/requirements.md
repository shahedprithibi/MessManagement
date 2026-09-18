# MessManagement — Requirements

## 1. Project Purpose

MessManagement is an application for managing shared meals and household expenses in bachelor messes, hostels, and similar shared living arrangements.

The system will help members:

- Record daily meals.
- Record guest meals.
- Record member contributions.
- Calculate the monthly meal cost.
- Calculate each member’s total expense.
- Show whether each member should receive a refund or pay additional money.
- Preserve monthly records for future reference.

## 2. Core Calculation Rules

For each month, the system will calculate the meal cost using the following process:

1. Add all member contributions for the month.
2. Count the total number of meals recorded for the month.
3. Calculate the cost of one meal:

   `Meal Cost = Total Contributions ÷ Total Meals`

4. Calculate each member’s meal expense:

   `Member Meal Expense = Member Meal Count × Meal Cost`

5. Calculate each member’s balance:

   `Balance = Member Contribution − Member Meal Expense`

The balance will be interpreted as follows:

- Positive balance: the member should receive money back.
- Negative balance: the member needs to pay additional money.
- Zero balance: the member’s contribution matches their meal expense.

## 3. Calculation Edge Cases

### 3.1 No Meals Recorded

If no meals are recorded for a month:

- The system must not divide by zero.
- The system must show that the meal cost cannot be calculated.
- The system must not generate normal member balances automatically.
- An administrator must review the situation.

### 3.2 No Contributions Recorded

If no contributions are recorded but meals exist:

- The calculated meal cost will be zero based on the current recorded data.
- Each member’s calculated meal expense will initially be zero.
- The system must clearly warn that contributions have not been recorded.
- The administrator must review the missing contribution records before closing the month.

### 3.3 Rounding

The system must use a consistent rounding policy for meal costs and member balances.

The exact rounding precision and currency rules will be decided during the technical design phase.

## 4. Users, Groups, and Roles

### 4.1 User Accounts

The system will support user accounts so that each person can access their own information securely.

A user account may contain:

- Name
- Email address or phone number
- Password or another supported authentication method
- Account status

### 4.2 Mess Groups

A user can belong to one or more mess groups.

Each mess group will have:

- A group name
- A list of members
- An administrator
- Monthly meal and contribution records
- Monthly calculation history

### 4.3 Member Role

A normal member can:

- View the mess information.
- Record their own meals.
- View their own contributions.
- View monthly calculations.
- View their balance and payment status.

### 4.4 Administrator Role

An administrator can:

- Create and manage a mess group.
- Add or remove members.
- Manage member roles.
- Record or edit contributions.
- Review and correct meal records.
- Review monthly calculations.
- Close a month.
- View previous monthly records.

## 5. Meal Record Permissions

### 5.1 Member Permissions

Members can:

- Add their own meal records.
- Edit their own meal records.
- Cancel their own meal records.
- View their own meal history.
- View the meal records allowed by the mess group’s privacy rules.

Members cannot:

- Edit another member’s meal records.
- Cancel another member’s meal records.
- Change records after the allowed correction period.

### 5.2 Administrator Permissions

Administrators can:

- View every member’s meal records in their mess group.
- Add, edit, or cancel meal records for any member.
- Correct incorrect or missing meal records.
- Review meal records before monthly calculation.
- Manage records after the member correction period has ended.

### 5.3 Meal Finalization and Correction Windows

The system will use two separate time windows for meal records.

#### Member Window: First 24 Hours

During the first 24 hours after the relevant meal period:

- Members can add their own meal records.
- Members can edit their own meal records.
- Members can cancel their own meal records.
- Members must submit their changes before the window closes.

After this 24-hour window, members can no longer modify that meal record.

#### Automatic Finalization

After the first 24 hours:

- The system will automatically finalize the meal record based on the submitted meal information.
- Any meal that remains selected will be recorded.
- Any meal that was properly cancelled before the deadline will not be recorded.
- The record will enter the administrator correction window.

#### Administrator Window: Following 24 Hours

During the 24 hours after automatic finalization:

- Only administrators can add, edit, or cancel the finalized meal record.
- Administrators can correct mistakes reported by members.
- Administrators can review all member records.
- The system should record who made each administrative correction and when it happened.

#### Permanent Lock

After the administrator correction window ends:

- The meal record becomes permanently locked.
- Members cannot change it.
- Administrators cannot directly edit or delete it through normal application actions.
- The system must preserve the finalized record for monthly calculations and history.

The complete normal correction period is therefore 48 hours from the relevant meal period:

- First 24 hours: member correction window.
- Next 24 hours: administrator correction window.
- After 48 hours: permanent lock.

## 6. Meal-Day and Meal-Period Rules

### 6.1 Meal-Day Definition

A meal day is a configurable 24-hour period defined by the mess
administrator.

The meal day begins at the configured daily cutoff time and ends
immediately before the same cutoff time on the following day.

For example, if the cutoff is 6:00 AM:

- Meal day begins at 6:00 AM.
- Meal day ends at 5:59:59 AM the following calendar day.
- Meals recorded during this period belong to the same meal day.

The cutoff time must be configurable for each mess group.

### 6.2 Meal Formats

Each mess group must define its active meal format.

Possible formats include:

- Breakfast only
- Lunch only
- Dinner only
- Breakfast and lunch
- Lunch and dinner
- Breakfast and dinner
- Breakfast, lunch, and dinner

The system should allow the administrator to configure which meal
periods are active.

### 6.3 Meal Records

For each active meal period, a member may:

- Record that they will take the meal.
- Cancel their own meal during the member correction window.
- View their submitted meal status.
- View the meal status for the relevant meal day.

A meal record must be associated with:

- Mess group
- Member
- Meal day
- Meal period
- Record status
- Creation time
- Last modification time

### 6.4 Meal Correction Timeline

For each meal day:

- During the first 24 hours, members may add, edit, or cancel their own
  meal records.
- After the first 24 hours, the system finalizes the submitted meal
  records automatically.
- During the following 24 hours, only administrators may correct meal
  records.
- Administrator corrections must record which administrator made the
  change and when the change was made.
- After 48 hours, the meal records become permanently locked.
