import numpy as np
import matplotlib.pyplot as plt
class Stock_Manager:
    def __init__(self):
        self.stocks = {
            'MRFT': {'name': 'MRF Tyres.', 'price': 250.0, 'quantity': 20},
            'G': {'name': 'Google', 'price': 2750.0, 'quantity': 15},
            'ONGC': {'name': 'ONGC', 'price': 8000.0, 'quantity': 5},
            'HB': {'name': 'HDFC BANK', 'price': 350.0, 'quantity': 10},
            'MSFT': {'name': 'Microsoft Corporation', 'price': 300.0, 'quantity': 12},
            'GOLB': {'name': 'Gold Bees', 'price': 60.72, 'quantity': 18},
            'TCS': {'name': 'Tata', 'price': 3921.0, 'quantity': 3},
            'INFY': {'name': 'Infy', 'price': 1425.0, 'quantity': 10},
            'HLVR': {'name': 'HinduUnitedlivr', 'price': 1021.0, 'quantity': 4},
            'WL': {'name': 'Winsol', 'price': 1000.0, 'quantity': 15},
            'FTL': {'name': 'Finelisting', 'price': 900.0, 'quantity': 5},
            'TGIF': {'name': 'Agribusiness', 'price': 1500.0, 'quantity': 20}
        }#here I have given stock portfolio name,quantity and price(initialized)

    def view_portfoliovalue(self):
        total_value = sum(self.stocks[s]['price'] * self.stocks[s]['quantity'] for s in self.stocks)
        print(f"Total Portfolio Value: ${total_value:.2f}")

    def buy_stocks(self, symbol, quantity):
        if symbol in self.stocks:
            self.stocks[symbol]['quantity'] = self.stocks[symbol]['quantity'] + quantity
            print(f"Bought {quantity} shares of {self.stocks[symbol]['name']} ({symbol})")
        else:
            print("Invalid symbol.")

    def sell_stocks(self, symbol, quantity):
        if symbol in self.stocks and self.stocks[symbol]['quantity'] >= quantity:
            self.stocks[symbol]['quantity'] = self.stocks[symbol]['quantity'] - quantity
            print(f"Sold {quantity} shares of {self.stocks[symbol]['name']} ({symbol})")
        else:
            print("Symbol you used is invalid or insufficient quantity.")

    def view_portfolio(self):
        print("Portfolio:")
        for symbol, data in self.stocks.items():
            print(f"{data['name']} ({symbol}): {data['quantity']} shares")

    def plot_portfolio(self):
        symbols = list(self.stocks.keys())
        quantities = [self.stocks[s]['quantity'] for s in symbols]
        plt.plot(symbols,quantities,color="green")
        plt.xlabel('STOCK SYMBOL')
        plt.ylabel('QUANTITY OF STOCK')
        plt.title('PORTFOLIO LINE CHART')
        plt.grid(True)
        plt.show()

if __name__ == "__main__":
    stockportfoliomanager = Stock_Manager()

    while True:
        print("\nMenu:")
        print("1. View Portfolio Value ")
        print("2. Buy Stocks")
        print("3. Sell Stocks")
        print("4. View Portfolio")
        print("5. Plot Portfolio")
        print("6. Exit from STOCK PORTFOLIO TERMINAL")

        choice = input("Enter your choice: ")

        if choice == '1':
            stockportfoliomanager.view_portfoliovalue()
        elif choice == '2':
            print('''Stock symbols which are available in the portfolio are:
            1.MRFT
            2.G
            3.ONGC
            4.HB
            5.MSFT
            6.GOLB
            7.TCS
            8.INFY
            9.HLVR
            10.WL
            11.FTL
            12.TGIF''')
            symbol = input("Enter stock symbol: ").upper()
            quantity = int(input("Enter quantity to buy: "))
            stockportfoliomanager.buy_stocks(symbol, quantity)
        elif choice == '3':
            symbol = input("Enter stock symbol: ").upper()
            quantity = int(input("Enter quantity to sell: "))
            stockportfoliomanager.sell_stocks(symbol, quantity)
        elif choice == '4':
            stockportfoliomanager.view_portfolio()
        elif choice == '5':
            stockportfoliomanager.plot_portfolio()
        elif choice == '6':
            print('''Exiting from the Stock Portfolio Manager.
                 Thank you for using ! ''')
            break
        else:
            print("Invalid choice. Please choose again.") 
