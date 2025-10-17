

requisition_counter = 10000  # starting number (global variable)

def collect_staff_info():
    """Get staff information - demonstrates modularity and input handling."""
    global requisition_counter
    requisition_counter += 1  # increment ID number each time program runs

    # Collecting staff info using input (abstraction - hiding details)
    date = input("Enter date (dd/mm/yyyy): ")
    staff_id = input("Enter Staff ID: ")
    name = input("Enter Staff Name: ")

    # Return a dictionary (data encapsulation)
    return {
        "date": date,
        "staff_id": staff_id,
        "name": name,
        "requisition_id": requisition_counter
    }

def collect_items():
    """Ask for item names and prices, and calculate total cost."""
    total = 0
    print("\nEnter items (type 'done' when finished):")

    # Loop for repeated input - demonstrates iteration
    while True:
        item = input("Item name (or 'done'): ")
        if item.lower() == "done":
            break
        # Error handling could be added here (future improvement)
        price = float(input(f"Price for {item}: $"))
        total += price

    return total

def approve_requisition(total, staff_id, req_id):
    """Check if requisition is approved or pending - shows decision making."""
    if total < 500:
        status = "Approved"
        approval_ref = staff_id + str(req_id)[-3:]
    else:
        status = "Pending"
        approval_ref = None

    return status, approval_ref

def main():
    """Main function - controls program flow and output."""
    staff = collect_staff_info()
    total = collect_items()

    # Apply business logic (decision principle)
    status, approval_ref = approve_requisition(
        total, staff["staff_id"], staff["requisition_id"]
    )

    # Output summary (user-friendly output)
    print("\n--- Requisition Summary ---")
    print("Date:", staff["date"])
    print("Requisition ID:", staff["requisition_id"])
    print("Staff ID:", staff["staff_id"])
    print("Staff Name:", staff["name"])
    print("Total: $", total)
    print("Status:", status)
    if approval_ref:
        print("Approval Reference:", approval_ref)

# Run the program
main()
# Assign3
