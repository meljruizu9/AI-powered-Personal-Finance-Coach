# AI-powered-Personal-Finance-Coach
Develop an AI-driven personal finance app that analyzes user spending habits and provides personalized recommendations for saving and investing.
import pandas as pd
from sklearn.cluster import KMeans

class PersonalFinanceCoach:
    def __init__(self):
        self.spending_data = pd.DataFrame(columns=['Category', 'Amount'])

    def add_spending(self, category, amount):
        """Add a spending record."""
        self.spending_data = self.spending_data.append({'Category': category, 'Amount': amount}, ignore_index=True)

    def analyze_spending(self):
        """Analyze spending habits to identify areas for savings."""
        category_totals = self.spending_data.groupby('Category').sum()
        print("Total spending by category:\n", category_totals)

        # Identify high spending categories
        high_spending_categories = category_totals[category_totals['Amount'] > category_totals['Amount'].median()]
        print("\nHigh spending categories (above median):\n", high_spending_categories)

    def recommend_savings(self):
        """Provide savings recommendations based on spending habits."""
        # This is a placeholder for more sophisticated AI-driven analysis
        # For demo purposes, we'll use a simple heuristic:
        # If spending in 'Eating Out' category is high, recommend reducing it
        if 'Eating Out' in self.spending_data['Category'].values:
            eating_out_total = self.spending_data[self.spending_data['Category'] == 'Eating Out']['Amount'].sum()
            if eating_out_total > 100:  # Assuming the currency is in dollars and 100 is the threshold
                print("\nRecommendation: You're spending a lot on eating out. Consider cooking at home to save money.")

        # Placeholder for investment recommendations
        print("\nInvestment Recommendation: Based on your current savings, consider investing in a low-cost index fund.")

# Demo
coach = PersonalFinanceCoach()
coach.add_spending('Eating Out', 120)
coach.add_spending('Groceries', 90)
coach.add_spending('Utilities', 60)
coach.add_spending('Eating Out', 30)
coach.add_spending('Entertainment', 50)

coach.analyze_spending()
coach.recommend_savings()
