# AWS Full Stack Deployment with Load Balancing

A complete guide to deploying a React + Node.js application on AWS with Application Load Balancer for high availability and scalability.

## 🏗️ Architecture

- **Frontend**: React app served via Nginx on EC2
- **Backend**: Node.js/Express API on multiple EC2 instances
- **Load Balancer**: AWS Application Load Balancer (ALB)
- **Database**: MongoDB Atlas (recommended) or local MongoDB
- **DNS**: Route 53 (optional)

## 🚀 Quick Start

### Prerequisites
- AWS Account
- Node.js 18+
- SSH key pair
- Basic knowledge of AWS EC2

### Local Development

1. **Backend Setup**
```bash
cd backend
npm install
npm run dev
```

2. **Frontend Setup**
```bash
cd frontend
npm install
npm start
```

### AWS Deployment

Follow the detailed guides in `/aws-setup/` directory:

1. EC2 Setup - `aws-setup/ec2-setup.md`
2. Security Groups - `aws-setup/security-groups.md`
3. ALB Setup - `aws-setup/alb-setup.md`
4. Route 53 Setup - `aws-setup/route53-setup.md` (optional)

### Deployment Scripts

Use the deployment scripts in `/deployment/` directory:
```bash
# Deploy backend (run on each backend EC2 instance)
./deployment/backend-deploy.sh

# Deploy frontend (run on frontend EC2 instance)
./deployment/frontend-deploy.sh
```

## 📊 Features

- ✅ Load balanced backend with health checks
- ✅ Auto-scaling ready architecture
- ✅ High availability across multiple AZs
- ✅ Production-ready with PM2 process manager
- ✅ Nginx for frontend static file serving
- ✅ CORS enabled for cross-origin requests
- ✅ Environment-based configuration

## 🔒 Security Best Practices

- Never commit `.env` files or AWS credentials
- Keep EC2 key pairs secure
- Use IAM roles instead of access keys
- Configure security groups with minimal access
- Enable HTTPS with AWS Certificate Manager
- Regular security updates on EC2 instances

## 📝 Testing
```bash
# Test ALB endpoint
curl http://your-alb-dns.amazonaws.com/health

# Test load balancing (refresh multiple times)
curl http://your-alb-dns.amazonaws.com/api/data

# Check backend logs
pm2 logs backend

# Check frontend status
sudo systemctl status nginx
```

## 🤝 Contributing

Pull requests are welcome! Please follow the existing code style.

## 📄 License

MIT License - feel free to use this project for learning and production.
