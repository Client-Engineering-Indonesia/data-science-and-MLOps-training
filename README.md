# Data Science and MLOps Training with IBM watsonx

<img width="1920" height="366" alt="image" src="https://github.com/user-attachments/assets/a4ea5498-2e3f-4e15-abd3-b0d82c098bea" />

A comprehensive hands-on training program that guides you through the complete machine learning lifecycle using IBM watsonx platform - from data preparation to model deployment, monitoring, and extending with Agentic AI.

---

## 🎯 Overview

This training repository provides a structured learning path for building, deploying, and managing machine learning models in production using IBM watsonx. You'll work through real-world scenarios to predict customer repurchase behavior, implementing best practices for MLOps and AI governance.

**What You'll Learn:**
- Setting up watsonx projects and connections
- Exploratory data analysis and feature engineering
- Automated machine learning with AutoAI
- Model deployment and API integration
- AI governance and continuous monitoring
- Building conversational AI agents

---

## 📚 Lab Structure

### [Lab 01: Create Your First watsonx Project](./Lab%2001%20-%20Create%20your%20first%20watsonx%20project/README.md)
**Duration:** ~30 minutes

Set up your watsonx environment and establish connections to data sources.

**Key Topics:**
- Access watsonx platform
- Create API keys for authentication
- Set up watsonx project
- Associate Watson Machine Learning service
- Configure Db2 database connection
- Set up Cloud Object Storage connection

**Skills Gained:**
- Platform navigation
- Resource provisioning
- Connection management
- Security configuration

---

### [Lab 02: Perform EDA and Feature Engineering](./Lab%2002%20-%20Perform%20EDA%20and%20feature%20engineering/README.md)
**Duration:** ~60 minutes

Analyze customer transaction data and engineer features for machine learning.

**Key Topics:**
- Create SPSS Modeler flow
- Exploratory data analysis
- Time-based feature aggregations
- Feature store creation
- Data transformation pipelines

**Skills Gained:**
- Visual data flow design
- Statistical analysis
- Feature engineering techniques
- Data quality assessment
- Feature store management

---

### [Lab 03: Develop and Deploy ML Model](./Lab%2003%20-%20Develop%20and%20deploy%20ML%20model/README.md)
**Duration:** ~45 minutes

Build and deploy a machine learning model using AutoAI for customer repurchase prediction.

**Key Topics:**
- AutoAI experiment creation
- Binary classification configuration
- Model training and evaluation
- Deployment space setup
- Online endpoint creation
- API testing

**Skills Gained:**
- Automated machine learning
- Model selection and tuning
- Deployment strategies
- REST API integration
- Model versioning

---

### [Lab 04: Monitor and Govern Live Model](./Lab%2004%20-%20Monitor%20and%20govern%20live%20model/README.md)
**Duration:** ~60 minutes

Implement continuous monitoring and governance for your deployed model.

**Key Topics:**
- watsonx.governance configuration
- Fairness monitoring setup
- Quality metrics tracking
- Drift detection
- Model explainability (LIME)
- Performance evaluation

**Skills Gained:**
- AI governance practices
- Bias detection and mitigation
- Model monitoring
- Explainable AI
- Compliance management

---

### [Lab 05: Extend MLOps with Agentic AI](./Lab%2005%20-%20Extend%20MLOps%20with%20Agentic%20AI/README.md)
**Duration:** ~75 minutes

Create an AI agent that provides conversational access to your ML model.

**Key Topics:**
- AgentLab setup
- Custom tool development
- Python function integration
- Natural language processing
- API endpoint integration
- Agent deployment

**Skills Gained:**
- Agentic AI development
- Custom tool creation
- API orchestration
- Conversational interfaces
- Agent deployment

---

## 🎓 Learning Path

```
Lab 01: Setup & Connections
    ↓
Lab 02: Data Analysis & Feature Engineering
    ↓
Lab 03: Model Development & Deployment
    ↓
Lab 04: Monitoring & Governance
    ↓
Lab 05: Agentic AI Extension
```

---

## 🛠️ Technologies Used

- **IBM watsonx.ai**: AI development platform
- **IBM watsonx.governance**: AI governance and monitoring
- **AutoAI**: Automated machine learning
- **SPSS Modeler**: Visual data flow design
- **AgentLab**: Conversational AI development
- **Cloud Object Storage**: Data storage
- **Db2**: Database management
- **Python**: Custom function development
- **REST APIs**: Model integration

---

## 📋 Prerequisites

### Required Access
- IBM Cloud account
- watsonx.ai access
- watsonx.governance access
- Cloud Object Storage instance
- Db2 database instance

### Technical Skills
- Basic understanding of machine learning concepts
- Familiarity with Python (for Lab 05)
- Basic SQL knowledge (helpful but not required)
- Understanding of REST APIs (helpful but not required)

### Software Requirements
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection
- Text editor (for viewing/editing code)

---

## 🚀 Getting Started

1. **Clone this repository:**
   ```bash
   git clone https://github.com/Client-Engineering-Indonesia/data-science-and-MLOps-training.git
   cd data-science-and-MLOps-training
   ```

2. **Start with Lab 01:**
   - Navigate to [Lab 01](./Lab%2001%20-%20Create%20your%20first%20watsonx%20project/README.md)
   - Follow the step-by-step instructions
   - Complete all steps before moving to the next lab

3. **Progress sequentially:**
   - Each lab builds on the previous one
   - Complete labs in order for best results
   - Save your credentials and IDs for later labs

---

## 📊 Use Case: Customer Repurchase Prediction

Throughout this training, you'll work on a real-world business problem:

**Business Challenge:**
Predict whether customers will make repeat purchases based on their transaction history.

**Data:**
- Customer transaction records
- Purchase amounts and frequencies
- Time-based aggregations (3, 6, 12 months)
- Customer demographics

**Solution:**
- Binary classification model (Will Repurchase: Y/N)
- Real-time prediction API
- Monitored for fairness and quality
- Accessible via conversational AI

**Business Value:**
- Identify high-value customers
- Optimize marketing campaigns
- Improve customer retention
- Enable data-driven decisions

---

## 🎯 Learning Outcomes

By completing this training, you will be able to:

✅ **Set up and configure** watsonx projects and connections  
✅ **Perform exploratory data analysis** and feature engineering  
✅ **Build and deploy** machine learning models using AutoAI  
✅ **Implement AI governance** with continuous monitoring  
✅ **Detect and mitigate bias** in ML models  
✅ **Create explainable AI** solutions using LIME  
✅ **Develop conversational AI agents** for model access  
✅ **Integrate ML models** with applications via APIs  
✅ **Monitor model performance** in production  
✅ **Apply MLOps best practices** throughout the ML lifecycle

---

## 📖 Additional Resources

### IBM watsonx Documentation
- [watsonx.ai Overview](https://www.ibm.com/docs/en/watsonx/saas?topic=overview)
- [AutoAI Documentation](https://www.ibm.com/docs/en/watsonx/saas?topic=models-autoai)
- [watsonx.governance Guide](https://www.ibm.com/docs/en/watsonx/saas?topic=governance-overview)
- [AgentLab Documentation](https://www.ibm.com/docs/en/watsonx/saas?topic=agents-overview)

### Learning Resources
- [IBM watsonx Learning Path](https://www.ibm.com/training/watsonx)
- [MLOps Best Practices](https://www.ibm.com/topics/mlops)
- [AI Governance Framework](https://www.ibm.com/topics/ai-governance)
- [Responsible AI Principles](https://www.ibm.com/artificial-intelligence/ethics)

### Community
- [IBM Developer Community](https://developer.ibm.com/)
- [watsonx Community Forum](https://community.ibm.com/community/user/watsonx/home)

---

## 🤝 Contributing

This training material is maintained by IBM Client Engineering Indonesia. For questions, issues, or suggestions:

1. Open an issue in this repository
2. Contact your training instructor
3. Reach out to IBM Client Engineering team

---

## 📝 License

This training material is provided for educational purposes. Please refer to IBM's terms of service for watsonx platform usage.

---

## 🏆 Completion Certificate

Upon completing all 5 labs, you will have:
- Built an end-to-end ML solution
- Implemented MLOps best practices
- Created a production-ready AI system
- Gained hands-on experience with IBM watsonx

**Next Steps:**
- Apply these skills to your own projects
- Explore advanced watsonx features
- Join the IBM watsonx community
- Continue learning with IBM training resources

---

## 📞 Support

For technical support during the training:
- Refer to lab-specific README files
- Check IBM watsonx documentation
- Contact your training instructor
- Visit IBM Support portal

---

**Happy Learning! 🚀**

*Last Updated: 2026*
