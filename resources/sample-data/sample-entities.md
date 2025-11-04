# Sample Entities Data

This document provides examples of custom entities you can create for your copilot, along with sample data for each.

## Closed List Entities

### 1. Product Categories

**Entity Name:** ProductCategory

**Items:**
| Item | Synonyms |
|------|----------|
| Electronics | electronics, tech, gadgets, devices, technology |
| Clothing | clothes, apparel, fashion, wear, garments |
| Home & Garden | home, garden, house, outdoor, furniture |
| Sports & Fitness | sports, fitness, exercise, workout, athletic |
| Books | books, reading, literature, novels, ebooks |
| Toys & Games | toys, games, kids, children, play |
| Food & Beverage | food, drinks, groceries, snacks, beverages |
| Beauty & Health | beauty, cosmetics, health, skincare, wellness |

### 2. Service Types

**Entity Name:** ServiceType

**Items:**
| Item | Synonyms |
|------|----------|
| Consultation | consult, consultation, advice, meeting, discussion |
| Repair | repair, fix, service, maintenance, restore |
| Installation | install, installation, setup, configure |
| Training | training, education, tutorial, lesson, workshop |
| Support | support, help, assistance, troubleshooting |
| Upgrade | upgrade, improve, enhance, update |

### 3. Priority Levels

**Entity Name:** PriorityLevel

**Items:**
| Item | Synonyms |
|------|----------|
| Critical | critical, urgent, emergency, immediate, asap |
| High | high, important, priority, soon |
| Medium | medium, normal, regular, standard |
| Low | low, minor, whenever, not urgent |

### 4. Department Types

**Entity Name:** Department

**Items:**
| Item | Synonyms |
|------|----------|
| Sales | sales, selling, purchase, buy |
| Support | support, help, customer service, assistance |
| Billing | billing, payment, invoice, accounting, finance |
| Technical | technical, IT, tech support, engineering |
| Human Resources | HR, human resources, personnel, people |
| Marketing | marketing, advertising, promotion, campaigns |

### 5. Issue Categories

**Entity Name:** IssueCategory

**Items:**
| Item | Synonyms |
|------|----------|
| Technical | technical, bug, error, system, software |
| Account | account, login, password, access, credentials |
| Billing | billing, payment, charge, subscription, invoice |
| Shipping | shipping, delivery, package, tracking |
| Product Quality | quality, defect, broken, damaged, faulty |
| Missing Items | missing, lost, not received, incomplete |
| Returns | return, refund, exchange, send back |

### 6. Appointment Times

**Entity Name:** AppointmentSlot

**Items:**
| Item | Synonyms |
|------|----------|
| Morning | morning, AM, before noon, early |
| Afternoon | afternoon, PM, after lunch, midday |
| Evening | evening, late afternoon, after work, night |

### 7. Size Options

**Entity Name:** Size

**Items:**
| Item | Synonyms |
|------|----------|
| Extra Small | XS, extra small, very small |
| Small | S, small |
| Medium | M, medium, regular |
| Large | L, large |
| Extra Large | XL, extra large, very large |
| XXL | XXL, 2XL, double XL |

### 8. Color Options

**Entity Name:** Color

**Items:**
| Item | Synonyms |
|------|----------|
| Black | black, dark |
| White | white, light |
| Red | red, crimson |
| Blue | blue, navy |
| Green | green, emerald |
| Yellow | yellow, gold |
| Gray | gray, grey, silver |
| Brown | brown, tan |

### 9. Payment Methods

**Entity Name:** PaymentMethod

**Items:**
| Item | Synonyms |
|------|----------|
| Credit Card | credit card, card, visa, mastercard, amex |
| Debit Card | debit card, bank card |
| PayPal | paypal, pay pal |
| Bank Transfer | bank transfer, wire transfer, direct transfer |
| Cash | cash, money, bills |
| Check | check, cheque |

### 10. Shipping Methods

**Entity Name:** ShippingMethod

**Items:**
| Item | Synonyms |
|------|----------|
| Standard | standard, regular, normal, ground |
| Express | express, fast, quick, rapid |
| Overnight | overnight, next day, 1-day |
| Two-Day | two day, 2-day, second day |
| International | international, overseas, global |

## Sample Smart Entity Examples

### 1. Product Names

**Entity Name:** ProductName

**Description:** Recognizes product names from user input

**Sample Training Phrases:**
- "I need help with my laptop"
- "My smartphone isn't working"
- "The tablet screen is cracked"
- "Issues with the wireless mouse"
- "The printer won't connect"
- "My headphones stopped working"
- "The smartwatch battery drains fast"
- "The keyboard keys are stuck"
- "Camera lens is scratched"
- "Monitor display is flickering"

### 2. Company Names

**Entity Name:** CompanyName

**Description:** Recognizes company or organization names

**Sample Training Phrases:**
- "I work at Microsoft"
- "Our company is Acme Corporation"
- "We're from Global Industries"
- "Tech Solutions Inc is my employer"
- "I represent Smith & Associates"

### 3. Address Components

**Entity Name:** StreetAddress

**Description:** Recognizes street addresses

**Sample Training Phrases:**
- "123 Main Street"
- "456 Oak Avenue"
- "789 Elm Boulevard"
- "1010 Park Drive"
- "2020 Market Street, Suite 100"

## Pre-built Entity Usage Examples

### Age Entity
- "I am 25 years old"
- "My age is 30"
- "I'm 45"

### Date and Time Entity
- "Tomorrow at 3 PM"
- "Next Monday"
- "December 25, 2024"
- "In two weeks"
- "This Friday at noon"

### Email Entity
- "john.doe@example.com"
- "contact@company.org"
- "support@business.net"

### Phone Number Entity
- "(555) 123-4567"
- "555-123-4567"
- "+1 555 123 4567"
- "5551234567"

### Number Entity
- "42"
- "one hundred"
- "3.14"
- "twenty-five"

### Currency Entity
- "$50"
- "100 dollars"
- "€25"
- "£40"

### Percentage Entity
- "25%"
- "fifty percent"
- "12.5%"

### URL Entity
- "https://www.example.com"
- "www.company.com"
- "http://blog.site.org"

## Custom Entity Best Practices

### 1. Naming Conventions
- Use PascalCase: `ProductCategory`, `ServiceType`
- Be descriptive and specific
- Avoid generic names like `Type` or `Category`

### 2. Synonym Guidelines
- Include common misspellings
- Add abbreviations
- Include plural forms
- Add related terms
- Consider regional variations

### 3. List Size Recommendations
- **Small lists**: 3-10 items (Priority, Size)
- **Medium lists**: 10-30 items (Product Categories)
- **Large lists**: 30-100 items (Product Names)
- **Very large lists**: Consider smart entities or database lookup

### 4. When to Use Which Type

**Closed List Entities:**
- Fixed set of options
- Predefined categories
- Multiple ways to express each option
- Examples: Colors, Sizes, Departments

**Smart Entities:**
- Open-ended possibilities
- Pattern recognition needed
- Cannot list all options
- Examples: Product names, Company names

**Pre-built Entities:**
- Standard data types
- No training needed
- Consistent formats
- Examples: Email, Phone, Date

## Testing Your Entities

### Test Cases to Validate

1. **Exact Match:**
   - User: "Electronics"
   - Should match: ProductCategory = Electronics

2. **Synonym Match:**
   - User: "I need tech help"
   - Should match: ProductCategory = Electronics

3. **Case Insensitive:**
   - User: "ELECTRONICS"
   - Should match: ProductCategory = Electronics

4. **Multiple Words:**
   - User: "I'm looking for home and garden items"
   - Should match: ProductCategory = Home & Garden

5. **No Match:**
   - User: "Something random"
   - Should not match any category

## Entity Validation Examples

### Validate Number Range
```
Variable: ProductQuantity
Entity: Number
Validation: 
  - Greater than 0
  - Less than or equal to 100
Error Message: "Please enter a quantity between 1 and 100"
```

### Validate Date in Future
```
Variable: AppointmentDate
Entity: Date and Time
Validation:
  - Is after System.CurrentDate
Error Message: "Please select a future date"
```

### Validate Email Domain
```
Variable: WorkEmail
Entity: Email
Validation:
  - Contains "@company.com"
Error Message: "Please use your company email address"
```

---

**Remember**: Well-designed entities improve accuracy and create better user experiences. Test thoroughly with real user inputs!
