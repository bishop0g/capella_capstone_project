# capella_capstone_project
Capstone project for Capella University; Flutter/Dart-based demo of cannabis POS program

# WEEK 1 NOTES:
## Database Sketching

Working on the values I'd need to populate a cannabis POS database.
So far the values could be formatted to work for a standard SQL DB. The only problem comes from separating packs of items, where there can be multiple values for a variable: representing these as lists because I know these can be represented in JSON just in case (I think Firebase focuses on NoSQL DBs anyway).

### Product Data:
- "UID": <str>, PRIMARY KEY ("1A4010300011621000026146")
- "Barcode" <str> ("PB22-0026146")
- "Category": "preroll", "flower", "extract," "pens", "edibles", "misc", "accessories" ("preroll")
- "SubCategory": "infused", "pack", "blunt", "None" ("pack")
- "BrandName": <str> ("Lifted Northwest")
- "LineName": <str> ("10x One Gram Cannabis Prerolls")
- "ProductName": <str> ("Day & Night 5 Indica + 5 Sativa")
- "StrainNames": list(<str>) ("Lemon Pie", "Double Gum")
- "StrainType": list("sativa", "indica", "hybrid") ("sativa", "indica")
- "UsableWeight": <float> (defaults to grams) (10.0)
- "THC": list(<float>) ("per serving") (19.99, 32.40)
- "CBD": list(<float>) ("per serving") (0.16, 0.0)
- "ServingsPer": <int> (10)
- "FarmName": list(<str>) ("Alibi Cannabis", "Wicked Kind")
- "FarmCode": list(<str>) ("020-1003391638A")
- "HarvestDate": list(<str>) ("7/1/2025", "6/24/2025")
- "LabName": list(<str>) ("FREE LABORATORIES")
- "TestDate": list(<str>) ("8/20/2025", "9/3/2025")

### Customer Data
- "CustomerID": <int>, PRIMARY KEY
- "FirstName": <str>
- "LastName": <str>
- "EmailAddress": <str>
- "PhoneNumber": <int>
- "DOB": <str>
- "State": <str>
- "PhysicalID": <str> (can vary; DL, Tribal ID, Passport, etc.)
- "IsMedical": <bool>
- "Discounted": <bool> (for veterans, special customers, etc.)

### Employee Data
- "EmployeeID": <int>, PRIMARY KEY
- "CompanyID": <str>
- "FirstName": <str>
- "LastName": <str>
- "EmailAddress": <str>
- "PhoneNumber": <int>
- "DOB": <str>

### Cart Data
- "CartID": <int>, PRIMARY KEY
- "CustomerID": <str>
- "CartContents": dict(product.UID: amount)
- "RunningTotal": <float>
- "Status": "cancelled", "complete", "unfilled", "waiting"

### Transaction Data
- "TransactionID": <int>, PRIMARY KEY
- "CartID": <int>
- "CustomerID": <str>
- "EmployeeID": <str>
- "RunningTotal": <float>
- "Discounts": <float>
- "Taxes": <float>
- "FinalTotal": (RunningTotal - Discounts) + Taxes
- "PaymentType": "cash", "card"
- "Status": "cancelled", "complete", "open", "voided"
