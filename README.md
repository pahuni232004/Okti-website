# Okti Foundation - Donation System

A complete donation system with Razorpay integration for the Okti Foundation website.

## Features

- ✅ Fully responsive website design
- ✅ Razorpay payment integration
- ✅ Secure backend order creation
- ✅ Payment verification
- ✅ Mobile-optimized interface

## Setup Instructions

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Environment Variables

1. Copy `env.example` to `.env`:
```bash
cp env.example .env
```

2. Update `.env` with your Razorpay credentials:
```env
RAZORPAY_KEY_ID=rzp_test_your_key_id_here
RAZORPAY_KEY_SECRET=your_key_secret_here
PORT=3000
NODE_ENV=development
```

### 3. Start the Backend Server

```bash
# Development mode (with auto-restart)
npm run dev

# Production mode
npm start
```

The backend will run on `http://localhost:3000`

### 4. Serve the Frontend

You can serve the HTML files using any static file server:

```bash
# Using Python (if installed)
python -m http.server 8000

# Using Node.js serve package
npx serve .

# Using Live Server (VS Code extension)
# Right-click on index.html and select "Open with Live Server"
```

## API Endpoints

- `GET /health` - Health check
- `GET /api/razorpay-key` - Get Razorpay key for frontend
- `POST /api/create-order` - Create Razorpay order
- `POST /api/verify-payment` - Verify payment signature

## File Structure

```
OKTI/
├── index.html              # Homepage
├── about.html              # About page
├── donate.html             # Donation form
├── education.html          # Education programs
├── journey.html            # Foundation journey
├── policy.html             # Privacy policy
├── payment-screen-1.html   # Payment interface
├── payment-screen-2.html   # Success page
├── styles.css              # All styles            
├── package.json            # Dependencies
├── env.example             # Environment template
└── README.md               # This file
```

## Security Notes

- Never expose your Razorpay Key Secret in frontend code
- Always verify payments on the backend
- Use HTTPS in production
- Store sensitive data securely

## Testing

1. Use Razorpay test credentials for development
2. Test with small amounts first
3. Verify payment flow end-to-end
4. Check error handling scenarios

## Production Deployment

1. Replace test credentials with live ones
2. Set up proper environment variables
3. Use HTTPS for all communications
4. Implement proper logging and monitoring
5. Set up database for storing donation records

## Deploying on Vercel

This project is ready to deploy on Vercel as a static site with serverless API routes for Razorpay.

### Environment Variables (Vercel Project Settings → Environment Variables)

- `RAZORPAY_KEY_ID` – Your Razorpay key id
- `RAZORPAY_KEY_SECRET` – Your Razorpay key secret

Optional (for email notifications on successful payment):

- `SMTP_HOST` – SMTP server host (e.g., smtp.gmail.com)
- `SMTP_PORT` – SMTP server port (e.g., 587)
- `SMTP_SECURE` – `true` to use TLS on port 465, otherwise `false`
- `SMTP_USER` – SMTP username
- `SMTP_PASS` – SMTP password
- `MAIL_FROM` – From address for emails (fallbacks to SMTP_USER)

No other variables are required for deployment.

### What was added for Vercel

- `api/razorpay-key.js` – returns public key for frontend
- `api/create-order.js` – creates Razorpay order on serverless function
- `api/verify-payment.js` – verifies payment signature
- `vercel.json` – config to build static assets and API routes
- `Anual Reports/index.html` – browsable index for reports directory

### One-click Deploy

1. Push this folder to a Git repository (GitHub/GitLab/Bitbucket)
2. Import the repo in Vercel
3. Add the two environment variables above
4. Deploy

After deployment, the website will be available at your Vercel URL, and the frontend will call the serverless endpoints at `/api/*`.

## Support

For issues or questions, contact the development team.

