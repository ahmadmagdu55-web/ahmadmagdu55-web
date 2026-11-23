# Tajer Home

Tajer Home is an Arabic-first SaaS platform for homeware retailers in Egypt. It helps merchants manage products, inventory, sales, purchases, expenses, debts, dashboard reporting, and subscription lifecycle from one professional workspace.

## Features
- Business registration and tenant isolation
- Product catalog with stock levels and pricing
- Sales and purchase workflows
- Supplier and customer records
- Expense tracking
- Inventory movement history
- Dashboard summary and basic reports
- RTL Arabic user interface
- Free trial, monthly, and annual subscription plans
- Manual payment verification and admin approval flow
- Subscription expiration enforcement on business operations
- Mobile-first responsive dashboard shell
- Installable PWA support

## Tech stack
- Laravel 12
- PHP 8.2
- MySQL/MariaDB compatible database
- React + TypeScript + Vite
- Tailwind CSS
- Sanctum

## Setup
```powershell
cd d:/my-project
composer install
copy .env.example .env
php artisan key:generate
php artisan migrate
php artisan db:seed
```

## Run the app
Backend:
```powershell
php artisan serve --host=127.0.0.1 --port=8000
```

Frontend:
```powershell
npm install
npm run dev -- --host 127.0.0.1 --port 5173
```

## Demo credentials
- Email: owner@example.com
- Password: Password123!

## Subscription defaults
- Trial plan: 7 days free
- Monthly subscription: 250 EGP
- Annual subscription: 2400 EGP
- Payment destination number: 01022809880

## Test commands
```powershell
php artisan test --filter=SubscriptionModuleTest
npm run build
```

## Default ports
- Laravel API: http://127.0.0.1:8000
- Vite frontend: http://127.0.0.1:5173

## Troubleshooting
- If MySQL login fails, create the database and update `.env`.
- If frontend scripts are blocked, temporarily bypass PowerShell execution policy for the session.
- If API requests fail, confirm the backend is running on port 8000 and the route includes `/api/v1`.
- If a subscription is expired, the backend blocks normal business operations until renewal or approval is complete.

