# Define the data lists
company_detail_list = [
    {'name': 'Company 1', 'domain': 'Retail', 'country': 'United States'},
    {'name': 'Company 2', 'domain': 'Technology', 'country': 'United Kingdom'},
    {'name': 'Company 3', 'domain': 'Healthcare', 'country': 'United States'}
]

employee_detail_list = [
    {'name': 'EMP-0001', 'first_name': 'John', 'last_name': 'Doe', 'full_name': 'John Doe', 'company': 'Company 1', 'nationality': 'Australia'},
    {'name': 'EMP-0002', 'first_name': 'Tom', 'last_name': 'Smith', 'full_name': 'Tom Smith', 'company': 'Company 2', 'nationality': 'United States'},
    {'name': 'EMP-0003', 'first_name': 'Andrew', 'last_name': 'Sebastian', 'full_name': 'Andrew Sebastian', 'company': 'Company 3', 'nationality': 'United States'},
    {'name': 'EMP-0005', 'first_name': 'Ying Han', 'last_name': 'Tan', 'full_name': 'Ying Han Tan', 'company': 'Company 1', 'nationality': 'Australia'},
    {'name': 'EMP-0015', 'first_name': 'Kenneth', 'last_name': 'Ng', 'full_name': 'Kenneth Ng', 'company': 'Company 3', 'nationality': 'United States'},
    {'name': 'EMP-0018', 'first_name': 'Rubby', 'last_name': 'Lee', 'full_name': 'Rubby Lee', 'company': 'Company 2', 'nationality': 'Hong Kong'},
    {'name': 'EMP-0017', 'first_name': 'Robert', 'last_name': 'White', 'full_name': 'Robert White', 'company': 'Company 1', 'nationality': 'United Kingdom'}
]

# Task 1: Get the list of all Companies and sort by Company Name in reverse order
sorted_companies = sorted([{'name': company['name']} for company in company_detail_list], key=lambda x: x['name'], reverse=True)

# Task 2: Print all Domain values in every company
domain_statements = [f"{company['name']}: {company['domain']} ({company['country']})" for company in company_detail_list]

# Task 3: List all Employees work By company domain
employees_by_domain = {}
for company in company_detail_list:
    domain = company['domain']
    employees_by_domain[domain] = [
        emp['full_name'] for emp in employee_detail_list if emp['company'] == company['name']
    ]

# Task 4: Create a function that returns employees with their company country
def get_employees_with_country(employee_list, company_list):
    company_country_map = {company['name']: company['country'] for company in company_list}
    return [
        {'full_name': emp['full_name'], 'company': emp['company'], 'country': company_country_map[emp['company']]}
        for emp in employee_list
    ]

employees_with_country = get_employees_with_country(employee_detail_list, company_detail_list)

# Task 5: Create a function that returns companies with the count of employee nationalities
def get_company_nationality_counts(employee_list):
    nationality_counts = {}
    for emp in employee_list:
        company = emp['company']
        nationality = emp['nationality']
        if company not in nationality_counts:
            nationality_counts[company] = {}
        if nationality in nationality_counts[company]:
            nationality_counts[company][nationality] += 1
        else:
            nationality_counts[company][nationality] = 1
    return [{'company': company, 'employee_nationality': counts} for company, counts in nationality_counts.items()]

company_nationality_counts = get_company_nationality_counts(employee_detail_list)

# Output the results
sorted_companies, domain_statements, employees_by_domain, employees_with_country, company_nationality_counts

<!---
satriowibowo271/satriowibowo271 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
