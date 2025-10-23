# 🏥 Hospital Appointment Management System

A comprehensive healthcare management system with separate portals for patients and doctors, built with Next.js frontend and Node.js backend.

## ✨ Features

### Patient Portal
- 🔐 User authentication (Login/Register)
- 👨‍⚕️ Doctor search and filtering
- 📅 Appointment booking
- 💳 Payment processing
- 📱 Appointment management
- 👤 Profile management
- 📊 Appointment statistics

### Doctor Portal
- 🩺 Doctor dashboard
- 📋 Appointment management
- 👥 Patient information
- 📈 Statistics and analytics
- ⏰ Schedule management
- 📝 Notes and prescriptions

## 🚀 Quick Start

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or cloud)
- npm or yarn

### Backend Setup

1. **Navigate to backend directory**
   ```bash
   cd backend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   - Copy `config.env` and update the values:
   ```bash
   cp config.env .env
   ```
   - Update MongoDB URI and other configurations

4. **Start MongoDB**
   - Make sure MongoDB is running on your system
   - Default connection: `mongodb://localhost:27017/hospital_appointment_system`

5. **Seed the database (optional)**
   ```bash
   node scripts/seedData.js
   ```

6. **Start the backend server**
   ```bash
   npm run dev
   ```
   - Server will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to project root**
   ```bash
   cd ..
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm run dev
   ```
   - Frontend will run on `http://localhost:3000`

## 🔑 Demo Accounts

### Patient Account
- **Email:** demo@hospital.com
- **Password:** demo123

### Doctor Account
- **Email:** ahmed.ali@hospital.com
- **Password:** doctor123

### Admin Account
- **Email:** admin@hospital.com
- **Password:** admin123

## 📱 Usage

### For Patients
1. Visit `http://localhost:3000`
2. Register a new account or use demo credentials
3. Browse doctors by specialty
4. Book appointments
5. Manage your appointments
6. View your profile and statistics

### For Doctors
1. Visit `http://localhost:3000/doctor`
2. Login with doctor credentials
3. View your dashboard with statistics
4. Manage appointments
5. Update appointment status
6. Add notes and prescriptions

## 🛠️ API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user
- `PUT /api/auth/profile` - Update profile
- `POST /api/auth/logout` - Logout

### Doctors
- `GET /api/doctors` - Get all doctors
- `GET /api/doctors/specialties` - Get specialties
- `GET /api/doctors/:id` - Get single doctor
- `POST /api/doctors` - Create doctor (Admin)
- `PUT /api/doctors/:id` - Update doctor (Admin)
- `DELETE /api/doctors/:id` - Delete doctor (Admin)

### Appointments
- `POST /api/appointments` - Book appointment
- `GET /api/appointments` - Get user appointments
- `GET /api/appointments/:id` - Get single appointment
- `PUT /api/appointments/:id/status` - Update status
- `PUT /api/appointments/:id/payment` - Update payment
- `DELETE /api/appointments/:id` - Cancel appointment

### Doctor Dashboard
- `GET /api/doctor/appointments` - Get doctor appointments
- `GET /api/doctor/dashboard/stats` - Get statistics
- `PUT /api/doctor/appointments/:id/status` - Update appointment
- `GET /api/doctor/schedule` - Get schedule

### Users
- `GET /api/users/stats` - Get user statistics
- `GET /api/users` - Get all users (Admin)
- `PUT /api/users/:id/status` - Update user status (Admin)

## 🗄️ Database Schema

### Users Collection
```javascript
{
  fullName: String,
  email: String (unique),
  password: String (hashed),
  phone: String,
  age: Number,
  gender: String,
  address: String,
  role: String (patient/admin),
  isActive: Boolean,
  lastLogin: Date,
  createdAt: Date,
  updatedAt: Date
}
```

### Doctors Collection
```javascript
{
  name: String,
  specialty: String,
  qualification: String,
  experience: String,
  fees: Number,
  rating: Number,
  patients: Number,
  available: [String],
  timeSlots: [String],
  image: String,
  color: String,
  bio: String,
  isActive: Boolean,
  contactInfo: {
    phone: String,
    email: String
  },
  createdAt: Date,
  updatedAt: Date
}
```

### Appointments Collection
```javascript
{
  doctor: ObjectId (ref: Doctor),
  patient: ObjectId (ref: User),
  bookingDetails: {
    date: Date,
    time: String,
    symptoms: String
  },
  payment: {
    amount: Number,
    method: String,
    status: String,
    transactionId: String,
    paymentDate: Date
  },
  status: String,
  notes: String,
  prescription: String,
  followUpDate: Date,
  cancelledBy: String,
  cancellationReason: String,
  createdAt: Date,
  updatedAt: Date
}
```

## 🔧 Configuration

### Environment Variables
```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database Configuration
MONGODB_URI=mongodb://localhost:27017/hospital_appointment_system

# JWT Configuration
JWT_SECRET=your_super_secret_jwt_key_here
JWT_EXPIRE=7d

# Frontend URL
FRONTEND_URL=http://localhost:3000
```

## 🚀 Deployment

### Backend Deployment
1. Set up MongoDB Atlas or use a cloud MongoDB service
2. Update environment variables for production
3. Deploy to platforms like Heroku, Railway, or DigitalOcean

### Frontend Deployment
1. Build the application: `npm run build`
2. Deploy to Vercel, Netlify, or any static hosting service

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

For support and questions:
- Create an issue in the repository
- Contact the development team

## 🔮 Future Enhancements

- [ ] Real-time notifications
- [ ] Video consultation
- [ ] Prescription management
- [ ] Medical records
- [ ] SMS/Email notifications
- [ ] Payment gateway integration
- [ ] Mobile app
- [ ] Multi-language support

---

Made with ❤️ for better healthcare management
