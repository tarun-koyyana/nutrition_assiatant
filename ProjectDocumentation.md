# 🍎 Nutrition Assistant Documentation

## 1. Project Overview

This document provides a comprehensive overview of the Nutrition Assistant web application. This full-stack project is designed to help users manage their nutrition, track meals, create personalized diet plans, and achieve their health goals.

## 2. Features

### User Management
- **User Registration & Authentication**: Secure user accounts with JWT tokens.
- **Profile Management**: Track personal stats (age, weight, height, BMI).
- **Health Goals**: Set and track fitness and nutrition objectives.
- **Dietary Preferences**: Manage allergies, restrictions, and preferences.

### Food Tracking
- **Comprehensive Food Database**: 20+ common foods with detailed nutritional information.
- **Meal Logging**: Track daily food consumption with nutritional calculations.
- **Nutritional Analysis**: Real-time calorie and macro tracking.
- **Search & Filter**: Find foods by category, dietary tags, and nutritional content.

### Diet Planning
- **Personalized Diet Plans**: AI-powered recommendations based on user profile.
- **Custom Meal Plans**: Create and manage weekly meal schedules.
- **Progress Tracking**: Monitor adherence to diet plans.
- **Goal-Based Recommendations**: Tailored plans for weight loss, muscle gain, or maintenance.

### Analytics & Insights
- **Daily Nutrition Summary**: Track calories, carbs, proteins, and fats.
- **BMI Calculator**: Monitor body mass index with health category indicators.
- **Progress Reports**: Visualize nutrition trends and goal progress.
- **Health Tips**: Personalized recommendations and nutrition advice.

## 3. Technical Architecture

### Frontend
- **React.js**: Modern UI with functional components and hooks.
- **React Router**: Client-side routing and navigation.
- **Axios**: HTTP client for API communication.
- **CSS3**: Modern styling with gradients, animations, and responsive design.

The client application was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

### Backend
- **Node.js**: Server-side JavaScript runtime.
- **Express.js**: Web application framework.
- **MongoDB**: NoSQL database with Mongoose ODM.
- **JWT**: JSON Web Tokens for authentication.
- **bcryptjs**: Password hashing and security.

## 4. Project Structure

```
c:\Users\WILIAM\Desktop\Nutrition-Assistant\
├───README.md
├───.git\...
├───client\
│   ├───.env
│   ├───.gitignore
│   ├───package-lock.json
│   ├───package.json
│   ├───README.md
│   ├───node_modules\...
│   ├───public\
│   │   ├───favicon.ico
│   │   ├───index.html
│   │   ├───logo192.png
│   │   ├───logo512.png
│   │   ├───manifest.json
│   │   └───robots.txt
│   └───src\
│       ├───App.css
│       ├───App.js
│       ├───App.test.js
│       ├───index.css
│       ├───index.js
│       ├───logo.svg
│       ├───reportWebVitals.js
│       ├───setupTests.js
│       ├───assets\
│       ├───components\
│       │   ├───Auth.css
│       │   ├───DietPlanCreator.css
│       │   ├───DietPlanCreator.js
│       │   ├───FoodAdder.css
│       │   ├───FoodAdder.js
│       │   ├───Home.css
│       │   ├───Home.js
│       │   ├───Login.js
│       │   ├───MealLogger.css
│       │   ├───MealLogger.js
│       │   ├───Register.js
│       │   ├───ReportsViewer.css
│       │   └───ReportsViewer.js
│       ├───pages\
│       ├───services\
│       └───utils\
└───server\
    ├───.env
    ├───index.js
    ├───package-lock.json
    ├───package.json
    ├───config\
    │   └───db.js
    ├───controllers\
    │   ├───authController.js
    │   ├───dietPlanController.js
    │   ├───foodController.js
    │   └───mealController.js
    ├───middleware\
    │   └───auth.js
    ├───models\
    │   ├───DietPlan.js
    │   ├───Food.js
    │   ├───Meal.js
    │   ├───NutritionFact.js
    │   └───User.js
    ├───node_modules\...
    ├───routes\
    │   ├───authRoutes.js
    │   ├───dietPlanRoutes.js
    │   ├───foodRoutes.js
    │   └───mealRoutes.js
    └───utils\
        └───seedData.js
```

## 5. Getting Started

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local installation or MongoDB Atlas)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Nutrition-Assistant
   ```

2. **Install server dependencies**
   ```bash
   cd server
   npm install
   ```

3. **Install client dependencies**
   ```bash
   cd ../client
   npm install
   ```

4. **Environment Setup**

   Create a `.env` file in the server directory:
   ```env
   MONGO_URI=mongodb+srv://<user>:<password>@<cluster-url>/<database-name>?retryWrites=true&w=majority
   JWT_SECRET=your-super-secret-jwt-key
   PORT=5000
   ```

5. **Seed the database**
   ```bash
   cd server
   node utils/seedData.js
   ```

6. **Start the development servers**

   **Terminal 1 - Start the backend server:**
   ```bash
   cd server
   npm start
   ```

   **Terminal 2 - Start the frontend development server:**
   ```bash
   cd client
   npm start
   ```

7. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000

## 6. API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user (protected)
- `PUT /api/auth/me` - Update user profile (protected)

### Foods
- `GET /api/foods` - Get all foods
- `GET /api/foods/:id` - Get specific food
- `POST /api/foods` - Add new food (admin)
- `PUT /api/foods/:id` - Update food (admin)
- `DELETE /api/foods/:id` - Delete food (admin)

### Meals
- `POST /api/meals` - Create meal (protected)
- `GET /api/meals` - Get user meals (protected)
- `GET /api/meals/daily-nutrition` - Daily nutrition summary (protected)
- `GET /api/meals/:mealId` - Get specific meal (protected)
- `PUT /api/meals/:mealId` - Update meal (protected)
- `DELETE /api/meals/:mealId` - Delete meal (protected)

### Diet Plans
- `POST /api/diet-plans` - Create diet plan (protected)
- `GET /api/diet-plans` - Get user diet plans (protected)
- `POST /api/diet-plans/recommend` - Generate recommended plan (protected)
- `GET /api/diet-plans/:dietPlanId` - Get specific plan (protected)
- `PUT /api/diet-plans/:dietPlanId` - Update plan (protected)
- `DELETE /api/diet-plans/:dietPlanId` - Delete plan (protected)

## 7. Database Schema

### User Collection
```javascript
{
  username: String (required, unique),
  email: String (required, unique),
  password: String (hashed),
  age: Number,
  weight: Number (kg),
  height: Number (cm),
  gender: String (enum),
  activityLevel: String (enum),
  dietaryPreferences: [String],
  allergies: [String],
  healthGoals: [String],
  createdAt: Date,
  updatedAt: Date
}
```

### Food Collection
```javascript
{
  name: String (required, unique),
  category: String (enum),
  calories: Number (per 100g),
  carbohydrates: Number,
  proteins: Number,
  fats: Number,
  fiber: Number,
  sugar: Number,
  vitamins: Object,
  minerals: Object,
  allergens: [String],
  dietaryTags: [String],
  description: String,
  isCommon: Boolean
}
```

## 8. Deployment

### Backend Deployment (Heroku)
1. Create Heroku app
2. Set environment variables
3. Deploy using Git
4. Configure MongoDB Atlas connection

### Frontend Deployment (Netlify/Vercel)
1. Build the React app: `npm run build`
2. Deploy build folder to hosting platform
3. Configure environment variables
4. Set up custom domain (optional)

## 9. Future Enhancements

- **Mobile App**: React Native version
- **Social Features**: Share meals and progress with friends
- **Barcode Scanner**: Scan food products for automatic logging
- **AI Recommendations**: Machine learning for personalized suggestions
- **Integration**: Connect with fitness trackers and health apps
- **Advanced Analytics**: Detailed nutrition reports and insights
- **Recipe Database**: User-generated and curated recipes
- **Meal Prep Planning**: Weekly meal preparation guides
