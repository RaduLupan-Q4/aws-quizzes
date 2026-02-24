# AWS Quizzes 🎯

Interactive quizzes to make learning AWS documentation more engaging and fun!

## About

This repository contains interactive, beautifully designed quizzes that help you learn AWS services by actually reading the official documentation. Each quiz is crafted to encourage thorough understanding rather than just memorization.

## Philosophy

AWS documentation can be dense and overwhelming. These quizzes are designed to:

- ✅ **Make learning fun** - Interactive UI with instant feedback
- ✅ **Encourage reading docs** - Questions require understanding, not just memorization
- ✅ **Test real scenarios** - Based on actual use cases and best practices
- ✅ **Provide explanations** - Learn from every question with detailed explanations and doc links
- ✅ **Track progress** - See your score, review incorrect answers, and improve

## Available Quizzes

### 1. FSx for ONTAP & SQL Server HA
**Focus**: SQL Server High Availability with Amazon FSx for NetApp ONTAP  
**Topics**: Multi-AZ deployments, HA pairs, iSCSI, MPIO, failover, disaster recovery, and best practices  
**Questions**: 20  
**Difficulty**: Intermediate to Advanced  
**[Take Quiz →](./fsx-ontap-sql-server-ha-quiz.html)**

### 2. AWS Fault Injection Service (FIS)
**Focus**: Chaos Engineering & Resilience Testing with AWS FIS  
**Topics**: Experiment templates, actions, targets, stop conditions, IAM roles, multi-account experiments, `aws:ssm:send-command`, emptyTargetResolutionMode, confused deputy protection  
**Questions**: 20  
**Difficulty**: Beginner to Intermediate  
**[Take Quiz →](./aws-fis-quiz.html)**

## Features

- 🎨 **Beautiful Dark Theme** - Easy on the eyes during long study sessions
- 📱 **Mobile Responsive** - Study anywhere, on any device
- ⏱️ **Exam Mode** - Timed practice with 50 minutes to simulate real exam pressure
- 📚 **Learn Mode** - Untimed learning with immediate feedback
- 🔀 **Shuffle Questions** - Random order to avoid memorization patterns
- 📊 **Detailed Results** - See your score breakdown and review incorrect answers
- 🔗 **AWS Doc Links** - Direct links to official AWS documentation for each question

## How to Use

1. **Visit the [quiz site](https://your-github-username.github.io/aws-quizzes/)**
2. **Choose a quiz** from the available list
3. **Select your mode**:
   - **Learn Mode**: Take your time, get instant feedback
   - **Exam Mode**: 50-minute timer, submit all answers at once
4. **Study the explanations** - Every question includes detailed explanations and links to AWS docs
5. **Review and improve** - Go through incorrect answers to strengthen your knowledge

## Quiz Format

Each quiz includes:
- **Multiple choice questions** based on real AWS scenarios
- **Detailed explanations** for both correct and incorrect answers
- **Official AWS documentation links** for deeper learning
- **Score tracking** and review capabilities

## Contributing

Have ideas for new quizzes or improvements? Feel free to:
- Open an issue with suggestions
- Submit a pull request with new quizzes
- Share feedback on existing quizzes

## Creating New Quizzes

### Using the Cursor AI Skill (Recommended)

This repository includes a [Cursor](https://cursor.sh) AI skill that automates quiz creation end-to-end. Open this project in Cursor, attach the `create-quiz` skill, then invoke it in the chat with one or more documentation URLs:

```
/create-quiz https://docs.aws.amazon.com/lambda/latest/dg/welcome.html
```

The skill will:
1. **Fetch and read** the provided AWS (or other) documentation pages
2. **Generate 20 questions** covering key concepts, best practices, edge cases, and real-world scenarios
3. **Create a standalone HTML file** (e.g. `aws-lambda-quiz.html`) in the project root, based on the gold standard template
4. **Validate** question structure, correct answer indexes, and documentation links

You can customise the output by adding parameters to the prompt:

| Parameter | Example | Default |
|-----------|---------|---------|
| Question count | `25 questions` | 20 |
| Quiz title | `title: "AWS Lambda"` | Inferred from docs |
| Badge label | `badge: "Lambda"` | Inferred from docs |
| Color scheme | `color: orange` | Suggested by topic area |

After the file is generated:
1. Add a card for the new quiz in `index.html` (follow the pattern of the existing cards)
2. Add an entry to the **Available Quizzes** section of this README
3. Commit and push — GitHub Pages will publish it automatically

### Manual Quiz Creation Guidelines

If you prefer to create a quiz by hand:
1. **Copy the template** — duplicate `fsx-ontap-sql-server-ha-quiz.html` and rename it
2. **Replace only the targeted fields** — title, badge, subtitle, accent colors, and the `questions` array
3. **Focus on real scenarios** — base questions on actual use cases, not trivial recall
4. **Encourage doc reading** — questions should require understanding, not just recognition
5. **Provide thorough explanations** — explain why wrong answers are wrong, not just why the correct one is right
6. **Link to official docs** — always include an AWS (or relevant) documentation URL per question
7. **Keep the HTML/JS structure intact** — do not modify element IDs, class names, or JavaScript logic

## License

These quizzes are provided as a free educational resource. The content is based on publicly available AWS documentation.

## Disclaimer

These quizzes are **unofficial** study resources created by the community. They are not affiliated with, endorsed by, or sponsored by Amazon Web Services (AWS). 

For official AWS certification preparation, please refer to:
- [AWS Certification Official Site](https://aws.amazon.com/certification/)
- [AWS Official Documentation](https://docs.aws.amazon.com/)
- [AWS Training and Certification](https://www.aws.training/)

## Support

Found these quizzes helpful? Consider:
- ⭐ **Starring this repository**
- 🔄 **Sharing with your colleagues**
- 💬 **Providing feedback** via issues
- 🤝 **Contributing** new quizzes

---

**Happy Learning! 🚀**

Made with ❤️ for the AWS community
