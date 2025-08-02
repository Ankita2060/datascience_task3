# datascience_task3
        from flask import Flask, request, jsonify
        import joblib

        app = Flask(__name__)
        model = joblib.load('your_model.pkl') # Load your trained model

        @app.route('/predict', methods=['POST'])
        def predict():
            data = request.json['data'] # Assuming input data is in JSON format
            prediction = model.predict([data]).tolist() # Make prediction
            return jsonify({'prediction': prediction})

        if __name__ == '__main__':
            app.run(debug=True)
                    from fastapi import FastAPI
        from pydantic import BaseModel
        import joblib

        app = FastAPI()
        model = joblib.load('your_model.pkl') # Load your trained model

        class Item(BaseModel):
            data: list # Define expected input data structure

        @app.post("/predict")
        async def predict(item: Item):
            prediction = model.predict([item.data]).tolist() # Make prediction
            return {"prediction": prediction}
            
