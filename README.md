##summary
import  pandas as pd
from sklearn.neighbors import NearestNeighbors

# Sample dataset: meals, calories, protein, carbon footprint
data = pd.DataFrame({
    'meal': ['Veggie Bowl', 'Chicken Salad', 'Tofu Stir Fry'],
    'calories': [500, 650, 550],
    'protein': [20, 40, 25],
    'carbon_kg': [1.2, 3.5, 0.8]
})

X = data[['calories', 'protein', 'carbon_kg']]
model = NearestNeighbors(n_neighbors=1)
model.fit(X)

# Find the closest meal for target preferences
target = [[550, 25, 1.0]]
distance, index = model.kneighbors(target)
print("Recommended meal:", data.iloc[index[0][0]]['meal'])
