# Funkce pro bezpečný vstup s čárkou nebo tečkou
def safe_input(prompt):
    user_input = input(prompt)
    # Nahrazení čárky za tečku
    user_input = user_input.replace(",", ".")
    try:
        return float(user_input)
    except ValueError:
        print("Neplatný vstup! Zadejte platné číslo.")
        return safe_input(prompt)

# Jazyková podpora
def choose_language():
    print("Vyberte jazyk / Choose language / Choisir une langue:")
    print("1: Čeština")
    print("2: English")
    print("3: Français")
    print("4: Español")
    choice = input("Zadejte číslo / Enter number: ")
    
    if choice == '1':
        return 'cz'
    elif choice == '2':
        return 'en'
    elif choice == '3':
        return 'fr'
    elif choice == '4':
        return 'es'
    else:
        print("Neplatná volba / Invalid choice")
        return choose_language()

# Překlady pro různé jazyky
translations = {
    'cz': {
        'welcome': "Vítejte v kalkulačce na výpočet plateb",
        'cost': "Kolik máte celkem zaplatit?",
        'tip': "Chcete přidat spropitné?",
        'tip_yes': "1: Ano",
        'tip_no': "2: Ne",
        'tip_type': "Jaký typ spropitného chcete zadat?",
        'tip_percentage': "1: Procento",
        'tip_fixed': "2: Pevná částka",
        'people': "Mezi kolik lidí se má rozdělit částka?",
        'currency': "Zvolte měnu, ve které chcete platit (CZK, EUR, USD, GBP, CFA):",
        'payment': "Každý člověk by měl zaplatit",
        'payment_method': "Jakým způsobem bude platba rozdělena? (Hotovost/Kreditní karta):",
        'individual_amounts': "Chcete zadat částky pro jednotlivé osoby? (A/N)",
        'skip_individual': "Pokud ne, částky budou rozděleny rovnoměrně.",
        'tip_total': "Zadejte celkovou částku spropitného, kterou chcete přidat k celkové částce:",
    },
    'en': {
        'welcome': "Welcome to the payment calculation app",
        'cost': "How much do you need to pay in total?",
        'tip': "Do you want to add a tip?",
        'tip_yes': "1: Yes",
        'tip_no': "2: No",
        'tip_type': "What type of tip would you like to set?",
        'tip_percentage': "1: Percentage",
        'tip_fixed': "2: Fixed amount",
        'people': "How many people should split the total amount?",
        'currency': "Choose the currency you want to pay with (CZK, EUR, USD, GBP, CFA):",
        'payment': "Each person should pay",
        'payment_method': "How will the payment be divided? (Cash/Credit Card):",
        'individual_amounts': "Do you want to enter individual amounts for each person? (Y/N)",
        'skip_individual': "If not, the amounts will be split equally.",
        'tip_total': "Enter the total tip amount you want to add to the total:",
    },
    'fr': {
        'welcome': "Bienvenue dans l'application de calcul des paiements",
        'cost': "Combien devez-vous payer au total?",
        'tip': "Voulez-vous ajouter un pourboire?",
        'tip_yes': "1: Oui",
        'tip_no': "2: Non",
        'tip_type': "Quel type de pourboire souhaitez-vous définir?",
        'tip_percentage': "1: Pourcentage",
        'tip_fixed': "2: Montant fixe",
        'people': "Combien de personnes doivent partager le montant total?",
        'currency': "Choisissez la devise avec laquelle vous souhaitez payer (CZK, EUR, USD, GBP, CFA):",
        'payment': "Chaque personne doit payer",
        'payment_method': "Comment le paiement sera-t-il divisé ? (Espèces/Credit Card):",
        'individual_amounts': "Voulez-vous entrer des montants individuels pour chaque personne ? (O/N)",
        'skip_individual': "Sinon, les montants seront divisés également.",
        'tip_total': "Entrez le montant total du pourboire que vous souhaitez ajouter au total:",
    },
    'es': {
        'welcome': "Bienvenido a la aplicación de cálculo de pagos",
        'cost': "¿Cuánto tienes que pagar en total?",
        'tip': "¿Quieres agregar una propina?",
        'tip_yes': "1: Sí",
        'tip_no': "2: No",
        'tip_type': "¿Qué tipo de propina te gustaría establecer?",
        'tip_percentage': "1: Porcentaje",
        'tip_fixed': "2: Cantidad fija",
        'people': "¿Cuántas personas deben dividir el monto total?",
        'currency': "Elija la moneda con la que desea pagar (CZK, EUR, USD, GBP, CFA):",
        'payment': "Cada persona debe pagar",
        'payment_method': "¿Cómo se dividirá el pago? (Efectivo/Tarjeta de crédito):",
        'individual_amounts': "¿Quiere ingresar cantidades individuales para cada persona? (S/N)",
        'skip_individual': "Si no, los montos se dividirán equitativamente.",
        'tip_total': "Ingrese el monto total de la propina que desea agregar al total:",
    }
}

# Výběr jazyka
language = choose_language()
lang_translations = translations[language]

# Funkce pro výpis výsledků
def print_summary(total_cost, one_payment, currency, lang):
    print(f"{lang['payment']}: {one_payment:.2f} {currency}")
    print(f"{lang['cost']}: {total_cost} {currency}")

# Hlavní program
print(lang_translations['welcome'])

# Základní vstupy s použitím safe_input pro čárky a tečky
cost = safe_input(lang_translations['cost'])
people = int(input(lang_translations['people']))

# Možnost přidat spropitné
tip_option = input(f"{lang_translations['tip']}\n{lang_translations['tip_yes']}\n{lang_translations['tip_no']}\n")
total_cost = cost  # Výchozí částka je pouze cena bez spropitného

if tip_option == "1":  # Pokud chceme přidat spropitné
    tip_type = input(f"{lang_translations['tip_type']}\n{lang_translations['tip_percentage']}\n{lang_translations['tip_fixed']}\n")
    if tip_type == "1":  # Procento
        percent = safe_input("Zadejte procento spropitného: / Enter tip percentage: ")
        total_cost += cost * percent / 100
    elif tip_type == "2":  # Pevná částka
        total_tip = safe_input(lang_translations['tip_total'])
        total_cost += total_tip
    else:
        print("Neplatná volba / Invalid choice")
        exit()

# Výběr měny pro platbu
currency = input(lang_translations['currency'])

# Výběr metody platby
payment_method = input(lang_translations['payment_method']).lower()

# Možnost zadání částek pro jednotlivé osoby
skip_individual = input(lang_translations['individual_amounts']).upper()
payments = []

if skip_individual == "S" or skip_individual == "Y":
    for i in range(people):
        payment = safe_input(f"Kolik zaplatí osoba {i + 1}? / How much will person {i + 1} pay? ")
        payments.append(payment)

# Pokud nebylo zadáno, rozdělí částku rovnoměrně
if not payments:
    one_payment = total_cost / people

# Zobrazení výsledků na základě zvoleného jazyka
print_summary(total_cost, one_payment, currency, lang_translations)
