# 🛍️ Laravel Store - E-Commerce Platform

Modern e-commerce platform built with Laravel 11, Vue 3, and Inertia.js. Features a complete shopping experience with admin panel, payment integration, and responsive design.

![Laravel](https://img.shields.io/badge/Laravel-11-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-3-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind-3-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.2-777BB4?style=for-the-badge&logo=php&logoColor=white)

## 🚀 Features

### Customer Features
- 🔐 **Authentication**: Register, login, social login (Google, GitHub)
- 🛒 **Shopping Cart**: Add, update, remove items with real-time updates
- ❤️ **Wishlist**: Save products for later
- 📦 **Product Catalog**: Browse by categories, brands with search and filters
- ⭐ **Reviews & Ratings**: Customer reviews with ratings
- 💳 **Secure Checkout**: Stripe payment integration
- 📍 **Address Management**: Multiple delivery addresses
- 📱 **Responsive Design**: Mobile-first approach

### Admin Features
- 📊 **Dashboard**: Powered by Filament Admin Panel
- 📝 **Product Management**: CRUD operations for products, categories, brands
- 🏷️ **Promo Codes**: Create and manage discount codes
- 📈 **Order Management**: Track and manage customer orders
- 👥 **User Management**: Manage customers and permissions

### Technical Features
- 🚄 **SPA Experience**: Using Inertia.js for seamless navigation
- 🔄 **Real-time Updates**: Laravel Horizon for queue management
- 🔍 **Monitoring**: Laravel Telescope for debugging
- 🐳 **Docker Support**: Ready-to-use Docker configuration
- 🗄️ **Database Support**: SQLite (default) or MySQL
- 🎨 **Modern UI**: Tailwind CSS with Flowbite components

## 📋 Requirements

- PHP >= 8.2
- Composer
- Node.js >= 18
- NPM or Yarn
- SQLite or MySQL

## 🛠️ Installation

### Option 1: Local Development (Laragon/XAMPP)

1. **Clone the repository**
```bash
git clone https://github.com/444rapz/laravel-store.git
cd laravel-store
```

2. **Install dependencies**
```bash
composer install
npm install
```

3. **Environment setup**
```bash
cp .env.example .env
php artisan key:generate
```

4. **Configure database in `.env`**
```env
# For SQLite (default)
DB_CONNECTION=sqlite

# For MySQL
# DB_CONNECTION=mysql
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=laravel_store
# DB_USERNAME=root
# DB_PASSWORD=
```

5. **Run migrations and seeders**
```bash
# Create SQLite database file (if using SQLite)
touch database/database.sqlite

# Run migrations with sample data
php artisan migrate:fresh --seed
```

6. **Build assets and start servers**
```bash
# Terminal 1 - Start Laravel server
php artisan serve

# Terminal 2 - Start Vite dev server
npm run dev

# Optional - Start queue worker
php artisan queue:work
```

7. **Access the application**
- Frontend: http://localhost:8000
- Admin Panel: http://localhost:8000/admin
- Default Admin: admin@brandford.com / password: brandford22

### Option 2: Docker Installation

1. **Clone and setup**
```bash
git clone https://github.com/444rapz/laravel-store.git
cd laravel-store
cp .env.example .env
```

2. **Build and run containers**
```bash
docker-compose up --build -d
```

3. **Install dependencies and migrate**
```bash
docker exec -it store-laravel composer install
docker exec -it store-laravel npm install
docker exec -it store-laravel php artisan key:generate
docker exec -it store-laravel php artisan migrate:fresh --seed
docker exec -it store-laravel npm run build
```

4. **Start Horizon (in separate terminal)**
```bash
docker exec -it store-laravel php artisan horizon
```

## 🔧 Configuration

### Payment Integration (Stripe)
Add to your `.env`:
```env
STRIPE_KEY=your_stripe_publishable_key
STRIPE_SECRET=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_webhook_secret
```

### Social Authentication
```env
# GitHub OAuth
GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_client_secret

# Google OAuth
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
```

### Mail Configuration
```env
MAIL_MAILER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=your_username
MAIL_PASSWORD=your_password
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=noreply@laravelstore.com
```

### Countries/States/Cities API
```env
CSC_API_URL=https://api.countrystatecity.in/v1/countries/
CSC_API_KEY=your_api_key
```

## 📁 Project Structure

```
laravel-store/
├── app/
│   ├── Filament/        # Admin panel resources
│   ├── Http/
│   │   ├── Controllers/  # API and web controllers
│   │   └── Middleware/   
│   ├── Models/           # Eloquent models
│   └── Enums/            # Application enums
├── database/
│   ├── factories/        # Model factories
│   ├── migrations/       # Database migrations
│   └── seeders/          # Database seeders
├── resources/
│   ├── js/              
│   │   ├── Components/   # Vue components
│   │   ├── Pages/        # Inertia pages
│   │   └── Layouts/      # Layout components
│   └── css/              # Stylesheets
├── routes/
│   ├── web.php           # Web routes
│   ├── api.php           # API routes
│   └── auth.php          # Authentication routes
└── docker/               # Docker configuration
```

## 🧪 Testing

Run the test suite:
```bash
# Run all tests
php artisan test

# Run with coverage
php artisan test --coverage
```

## 📚 Key Technologies

- **Backend**: Laravel 11, PHP 8.2
- **Frontend**: Vue 3, Inertia.js, TypeScript
- **Database**: SQLite/MySQL, Laravel Eloquent ORM
- **Admin Panel**: Filament 3
- **Styling**: Tailwind CSS, Flowbite
- **Payment**: Stripe, Laravel Cashier
- **Queue**: Laravel Horizon, Redis
- **Monitoring**: Laravel Telescope
- **Authentication**: Laravel Breeze, Socialite
- **Media**: Spatie Media Library
- **Containerization**: Docker, Docker Compose

## 🚢 Deployment

### Production Build
```bash
# Install production dependencies
composer install --optimize-autoloader --no-dev
npm ci

# Build assets
npm run build

# Cache configuration
php artisan config:cache
php artisan route:cache
php artisan view:cache

# Run migrations
php artisan migrate --force
```

### Environment Variables for Production
Ensure these are set in production:
```env
APP_ENV=production
APP_DEBUG=false
APP_URL=https://yourdomain.com
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## 👨‍💻 Author

**444rapz**
- GitHub: [@444rapz](https://github.com/444rapz)

## 🙏 Acknowledgments

- Laravel Team for the amazing framework
- Vue.js Team for the reactive framework
- Filament Team for the admin panel
- All contributors and package maintainers

---

<p align="center">Made with ❤️ using Laravel & Vue.js</p>