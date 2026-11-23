# Subscription Management

This application includes a SaaS subscription layer for business accounts. It is designed to support a free trial, paid monthly or annual plans, and a manual payment verification workflow for admin approval.

## Plan model

Subscribed businesses can use one active plan at a time. The platform stores plans in the `subscription_plans` table and supports the following default plan types:

- `trial`: 7-day free trial
- `monthly`: 250 EGP / month
- `yearly`: 2400 EGP / year

## Business lifecycle

When a new business is created, the platform automatically creates a free-trial subscription record. Re-creating or re-login does not restart the same business trial. The backend checks active subscription status before allowing normal business operations.

When a subscription or trial expires, the merchant remains able to access the platform only for subscription management and renewal steps. The business data stays intact and is not deleted.

## Payment verification flow

1. A business chooses a plan and submits a payment request with the transfer reference and proof image.
2. The request is saved as a pending payment under the relevant `subscription_id`.
3. A platform administrator reviews the payment and either approves or rejects it.
4. Approval activates the business subscription and extends the expiration date.
5. Rejection keeps the business on its prior status and records the admin reason.

## Admin controls

Only users with the platform role `admin` or `super_admin` can approve, reject, or adjust plan settings. The platform admin area displays a list of businesses and their current subscription state.

## Configuration

The payment destination number is configured in the frontend as `01022809880` and can be updated in the business subscription screen when the payment provider label is adjusted in the admin settings.

## API routes

The SaaS routes are available under `/api/v1`:

- `GET /subscription`
- `GET /subscription/plans`
- `GET /subscription/payments`
- `POST /subscription/payments`
- `GET /admin/subscriptions`
- `GET /admin/subscriptions/payments`
- `POST /admin/subscriptions/payments/{payment}/approve`
- `POST /admin/subscriptions/payments/{payment}/reject`
- `PUT /admin/subscriptions/plans/{plan}`

## Manual verification note

Proof upload does not automatically activate a subscription. It only creates a pending payment record that must be approved by the platform administrator.
