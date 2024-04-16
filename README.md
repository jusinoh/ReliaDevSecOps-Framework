## Planning and Threat Assessment

During the conceptual phase of software development, security is deeply integrated into the planning process through systematic threat modeling. This stage involves abstracting and visualizing the architecture to identify where sensitive data flows and potential vulnerabilities might exist. It focuses on key security concepts such as the principles of least privilege, defense in depth, and security by design (OWASP, 2010). By adopting a proactive approach and emphasizing continuous feedback and iterative improvements, teams ensure that security measures evolve with the development lifecycle and respond effectively to new threats.

**Secure Coding Practices:** Secure coding involves the disciplined approach to crafting software, systems, and applications aiming to prevent inadvertent incorporation of security weaknesses (UC Berkeley, n.d.).

- Requirement Identification and Compliance:
  - Overview: Identify and document security requirements upfront based on regulatory, legislative, or contractual needs, such as compliance with NIST 800-53 for government-related industries.
  - Purpose: Ensures that all security measures align with specific industry standards from the beginning of the project, facilitating compliance and effective risk management.

- Architectural Design and Data Workflow:
  - Overview: Opt for established libraries and frameworks over custom, unvetted solutions. Avoid architectures and data workflows that may introduce logical errors. Refrain from using outdated or insecure protocols for data transmission.
  - Purpose: Minimizes security vulnerabilities through the use of vetted solutions and secure communication protocols, thereby enhancing the overall security posture.

- Configuration Management:
  - Overview: Avoid using default security settings, such as outdated instance metadata versions in cloud deployments. Establish internal standards to ensure all configurations and resource attributes undergo thorough reviews to meet security best practices.
  - Purpose: Customized configurations prevent potential breaches and ensure systems are robust against attacks by eliminating commonly exploited settings.

- Input Validation and Data Integrity:
  - Overview: Implement stringent input validation processes including:
  - Validating data on trusted systems only.
  - Using centralized routines for application-wide input validation.
  - Standardizing data before validation (canonicalization).
  - Rejecting all inputs that do not meet validation criteria.
  - Ensuring all client-supplied data, including URLs and HTTP headers, are thoroughly validated against expected types and length specifications.
  - Purpose: Prevents data breaches and vulnerabilities such as SQL injection and XSS by ensuring only clean, validated data is processed.

- Output Encoding Practices:
  - Overview: Encode output based on the context of its display (HTML, URLs, JavaScript, etc.), employing trusted encoding libraries. Integrate automated encoding processes into CI/CD pipelines for consistency across applications.
  - Purpose: Protects against injection attacks and ensures safe rendering of content across different platforms and user interfaces.

- Credentials and Secrets Management:
  - Overview: Implement robust systems for managing credentials and secrets to ensure they are protected from unauthorized access and leaks.
  - Purpose: Secures sensitive information critical to the integrity and privacy of the application and user data.

- Comprehensive Access and Session Management:
  - Overview: Develop advanced mechanisms for controlling access to resources and managing user sessions to enhance security and operational control.
  - Purpose: Ensures that only authorized entities have access to specific resources and that user sessions are securely managed to prevent unauthorized access.

- Advanced Security Practices:
  - Overview: Integrate a suite of advanced security practices including cryptographic measures, error handling and logging, data protection, communication security, system configuration audits, database security, and secure file management.
  - Purpose: Addresses all layers of application and infrastructure security, providing a holistic defense against potential security threats.

**Initial Threat Modeling:** Threat modeling plays a pivotal role in DevSecOps by helping to detect, evaluate, and address potential threats to software systems and applications at the onset of the development phase (The GitLab Handbook, 2024). This process entails constructing a graphical depiction of the system, its assets, possible attack paths, and vulnerabilities.

- Identification of System Assets:
  - Overview: Clearly identify and document all critical assets within the system, which could include software components, data storage devices, and communication networks.
  - Purpose: Understanding what needs to be protected is the first step in safeguarding the system against attacks, ensuring that all valuable or sensitive assets are accounted for in the threat model.

- Mapping Potential Attack Paths:
  - Overview: Analyze and document possible attack vectors that could be exploited by attackers. This includes assessing common vulnerabilities and exposure points within the system’s design.
  - Purpose: Mapping out how an attacker could potentially breach the system allows developers and security teams to prioritize security measures based on the most likely threats.

- Vulnerability Identification:
  - Overview: Utilize various tools and techniques, such as automated scans and manual reviews, to identify vulnerabilities within the system that could be exploited.
  - Purpose: Proactive identification of weaknesses before they can be exploited improves the overall security posture and resilience of the system.

- Risk Assessment and Prioritization:
  - Overview: Evaluate the identified vulnerabilities in terms of their potential impact and the likelihood of exploitation. Prioritize remediation efforts based on this assessment.
  - Purpose: Efficiently allocate resources to address the most critical vulnerabilities first, reducing the system’s overall risk exposure.

- Mitigation Strategy Development:
  - Overview: Develop and document strategies to mitigate or eliminate identified risks. This may involve redesigning certain aspects of the system, implementing additional security controls, or enhancing existing measures.
  - Purpose: A well-defined mitigation strategy ensures that vulnerabilities are addressed before they can be exploited, enhancing the security of the system.

**Repository Hardening:** Repository hardening is the strategic enhancement of software repositories to shield against potential security threats and vulnerabilities (GitHub Docs, n.d.). It involves stringent access control measures such as role-based access controls and authentication to restrict access to sensitive information. Encryption techniques are employed to secure critical data at rest and in transit, while code signing verifies the authenticity and integrity of code changes. Secure communication protocols like HTTPS and SSH protect data exchanges, and regular vulnerability scanning helps identify and rectify security weaknesses promptly. The process also includes integrating thorough code reviews to catch and resolve security flaws, robust auditing and logging to monitor activities, and comprehensive backup and disaster recovery plans to ensure data resilience and continuity in adverse situations.

- Repository Access Management:
  - Overview: Clearly define and enforce who can access the repository and the extent of their permissions.
  - Purpose: Ensures that only authorized personnel have access to modify, view, or manage the repository, minimizing the risk of unauthorized changes or breaches.

- Dependency Management:
  - Overview: Utilize Software Bill of Materials (SBOM) inventory and Software Composition Analysis (SCA) tools to proactively identify vulnerabilities in the repository's dependencies.
  - Action: Leverage findings from these tools to generate alerts, alarms, and detailed reports that track vulnerabilities throughout their lifecycle.
  - Purpose: Helps maintain a secure development environment by ensuring that all third-party components are up-to-date and secure, thus preventing exploits from known vulnerabilities.

- Code Scanning and Review:
  - Overview: Employ code scanning tools that are specifically designed for the frameworks and libraries used in your system, software, or application.
  - Purpose: These tools can automatically detect security flaws, coding errors, and other vulnerabilities during the development phase, allowing for immediate remediation.

- Secrets Management:
  - Overview: Implement secrets detection tools to identify and manage sensitive information such as passwords, tokens, and API keys within the codebase.
  - Purpose: Prevents the accidental exposure of secrets, ensuring that sensitive data is encrypted and stored securely, compliant with best practices for information security.

**Secrets Management:** In CI/CD environments, secrets and variables have distinct but crucial roles (GitLab Docs, n.d.). Secrets, such as API tokens, database credentials, or private keys, are sensitive and must be carefully managed and specified within each job to prevent exposure. Variables, meanwhile, contain non-sensitive, environment-specific data and are accessible across all jobs without needing extra security measures. Ensuring the security of secrets is essential to preserve the integrity of the CI/CD process and to prevent unauthorized access and security breaches. For specific configuration guidelines in your CI/CD pipeline, refer to detailed resources like the GitLab CI/CD pipeline configuration reference.

- Overview of Secrets Management:
  - Overview: Secrets management is a critical component in CI/CD environments, crucial for protecting sensitive information required for continuous integration and deployment processes.
  - Purpose: Proper management of secrets ensures that sensitive data such as API tokens, database credentials, and private keys are securely stored, accessed, and used, preventing unauthorized acce  ss and data breaches.

- Identification and Classification of Secrets:
  - Overview: Clearly identify and classify data that qualifies as a secret within the CI/CD pipeline. This includes determining which information is sensitive and requires stringent security measures.
  - Purpose: Helps in applying the appropriate security controls to the right set of data, ensuring that only data classified as secrets are protected with enhanced security protocols.

- Secure Storage and Access of Secrets:
  - Overview: Implement secure storage solutions for secrets, utilizing tools and technologies designed for secure secret management. Ensure that access to secrets is strictly controlled and only granted to systems or personnel on a need-to-know basis.
  - Purpose: Secure storage and controlled access prevent unauthorized retrieval and use of secrets, reducing the risk of insider threats and external breaches.

- Integration of Secrets into CI/CD Pipelines:
  - Overview: Integrate secrets securely into CI/CD workflows, ensuring that they are injected into jobs without exposing them to unauthorized entities. Use automated tools to manage the distribution and lifecycle of secrets within the pipeline.
  - Purpose: Automating the handling of secrets within CI/CD pipelines reduces manual errors, enhances the efficiency of the deployment process, and maintains the confidentiality and integrity of secrets throughout the deployment cycle.

- Regular Audits and Rotation of Secrets:
  - Overview: Conduct regular audits to review access logs and usage patterns of secrets. Implement a routine rotation policy for secrets to limit the longevity of any single secret.
  - Purpose: Regular audits and rotation policies help in identifying unauthorized access or misuse of secrets early and mitigate potential damage by limiting the exposure time of compromised secrets.

- Delineation Between Secrets and Non-sensitive Variables:
  - Overview: Clearly distinguish between secrets and non-sensitive CI/CD variables, ensuring that each is handled according to its sensitivity level. Non-sensitive variables should be managed without the stringent security measures required for secrets.
  - Purpose: This differentiation ensures that resources are not unnecessarily secured, optimizing the management resources while focusing security efforts on truly sensitive information.

- Compliance and Best Practices:
  - Overview: Follow industry standards and compliance requirements for secrets management. Regularly update and align secrets management practices with best practices and regulatory guidelines.
  - Purpose: Compliance with industry standards and best practices enhances the security posture of the CI/CD environment and protects against legal and financial repercussions associated with data breaches.

## Code Development and Review

In the code development and review phase, maintaining a strong security framework through diverse testing and analysis strategies is crucial (Netflix TechBlog, 2022). The process kicks off with Commit-CI, where each code submission activates Continuous Integration systems, providing quick feedback on both integration results and security assessments. Key to this phase is static analysis, which includes Static Application Security Testing (SAST) for uncovering code vulnerabilities, Software Composition Analysis (SCA) for detecting risks in third-party components, and both scanning and hardening practices under Container Security to safeguard Docker and similar container technologies. Additionally, Infrastructure as Code (IaC) methods are carefully examined to protect provisioning scripts and manage configurations securely.

Progressing to Continuous Delivery (CD), the focus shifts to Dynamic Application Security Testing (DAST), which tests operational applications for vulnerabilities missed during static analysis. The phase also emphasizes specialized tests like Application Security Testing and API Security assessments, catering to the distinct security requirements of these platforms. Frequent Misconfiguration Checks help identify and correct any security mistakes in configurations, a frequent source of breaches. These thorough measures during the code development and review phase are designed to robustly shield applications from evolving security threats.

**Commit-CI Integration:**

- Overview: Incorporate security and reliability checks directly into the coding process, emphasizing code quality and integration of vulnerability scans during the initial stages of code commits.
- Purpose: Ensures that security and quality are foundational aspects of code development, reducing vulnerabilities early in the development lifecycle.

**Static Application Security Testing (SAST):**

- Overview: Employ tools that perform static analysis to detect vulnerabilities in code before it is compiled and executed.
- Purpose: Identifies potential security flaws within the codebase without having to run the application, enabling developers to make corrections early in the development process.

**Software Composition Analysis (SCA):**

- Overview: Analyze third-party components and libraries used within the application for known security vulnerabilities.
- Purpose: Ensures that all external components integrated into the application are secure and up to date, mitigating the risk of inheriting vulnerabilities from third-party resources.

**Infrastructure as Code (IaC) Scanning:**

- Overview: Scan infrastructure-as-code configurations to identify misconfigurations and compliance violations.
- Purpose: Enhances the security and compliance of automated infrastructure provisioning, supporting a secure deployment environment.

**Continuous Deployment (CD) Security:**

- Overview: Implement automated deployment processes that include rigorous security checks to ensure that releases are stable and secure.
- Purpose: Automates the deployment process while incorporating security as a critical checkpoint, thereby maintaining stability and security in production environments.

**Dynamic Application Security Testing (DAST):**

- Overview: Conduct security assessments on running applications to identify vulnerabilities that are only detectable during operation.
- Purpose: Complements static testing by identifying runtime vulnerabilities, offering a more comprehensive security evaluation.

**API Security Testing:**

- Overview: Systematically test APIs for security vulnerabilities and functional correctness to ensure robust interface communications.
- Purpose: Protects APIs from common vulnerabilities and ensures they function as intended, securing application integrations.

**Manual Code Reviews:**

- Overview: Integrate manual code reviews as a crucial part of the development process to capture issues that automated tools might overlook, such as logical errors or the misuse of internal APIs (Riggs, 2022).
- Purpose: Provides a layer of human oversight that can identify nuanced issues not caught by automated systems, fostering deeper insights into code quality and security. These reviews also promote best practices and mentorship among developers (Greene, 2019).

## Monitoring and Operation

In Site Reliability Engineering (SRE), effective operations and diligent monitoring are essential to secure and stabilize systems. Grounded in DevOps principles, SRE focuses on integrating automated processes to enhance operational efficiency. Central to this discipline is the formulation of Service Level Objectives (SLOs) that dictate monitoring and alerting protocols, ensuring systems perform in alignment with business expectations and user demands. These protocols are crucial for identifying issues proactively, allowing for timely interventions before system performance is impacted.

SRE also prioritizes minimizing toil—the elimination of repetitive, manual tasks through automation—thereby freeing up engineering resources for more complex, value-add activities. This shift not only improves operational efficiency but also enhances system security by reducing the likelihood of human error. Key operational practices within SRE include stringent on-call management, effective incident response, and comprehensive postmortems. These practices are fundamental in quickly addressing and learning from system failures, thus continually refining the reliability and security of the systems. Techniques such as load management, robust data processing architectures, and stringent configuration management are applied to further bolster system stability and performance. Moreover, deploying new features through methods like canary releases allows for careful, monitored rollouts that mitigate potential risks associated with new updates.

On a broader organizational scale, SRE promotes a culture of continuous improvement and cross-team collaboration, ensuring that practices not only support but also enhance system reliability and security. This approach fundamentally shapes how operations and monitoring are executed, positioning SRE as a crucial framework for securing and optimizing IT platforms.

**Overview of SRE Monitoring:**

- Overview: Monitoring within SRE focuses on creating resilient, efficient, and continuously improving systems that deliver high-quality services while adhering to business and regulatory standards.
- Purpose: Ensures systems not only remain operational but also thrive under constant improvement and adaptation, aligning with both user needs and compliance requirements.

**Site Reliability Engineering:**

- Overview: A dedicated phase that emphasizes enhancing system reliability through meticulous infrastructure management, proactive incident response, and ongoing optimization based on core SRE principles.
- Purpose: To instill a robust infrastructure that supports scalable, reliable, and optimal service delivery, critically underpinned by SRE methodologies.

**Monitoring and Incident Response:**

- Overview: Implement Service Level Objectives (SLOs) that are crucial in the SRE framework, derived from specific, quantitative Service Level Indicators (SLIs) such as request latency, error rates, and system throughput.
  - Note: Expand on this to address decoupling the application also means decoupling your logging efforts, creating dashboards to review each aspect of the application to understand which specific microservice is not behaving correctly.
- Purpose: These metrics ensure that the operational performance accurately mirrors user experiences, facilitating effective monitoring, management, and enhancements aligned with user expectations and organizational goals.

**Postmortems and Continuous Improvement:**

- Overview: Conduct blameless postmortems to analyze failures thoroughly using SLI data, translating these insights into actionable system improvements.
- Purpose: Encourages a culture of continuous learning and systemic enhancement, preventing future incidents and strengthening system reliability.

**Automation to Reduce Toil:**

- Overview: Leverage automation to minimize repetitive tasks, thereby freeing up SRE teams to focus on strategic initiatives that add significant business value.
- Purpose: Targets frequent issues indicated by SLIs to reduce operational toil and improve team efficiency and system performance.

**Change Management and Risk Reduction:**

- Overview: Utilize phased rollouts and comprehensive testing, guided by SLI insights, to manage changes and minimize potential system disruptions.
- Purpose: Enhances the stability of deployments and maintains service continuity even during significant updates and changes.

**Capacity Planning and Resource Management:**

- Overview: Prioritize precise capacity planning and resource management, using data from SLIs to make informed decisions regarding resource allocation and scalability.
- Purpose: Ensures the system can scale effectively and remain reliable under varying load conditions.

**Security and Compliance:**

- Overview: Integrate rigorous security measures into daily operations and strategic planning, with SLIs assisting in monitoring compliance with security standards.
- Purpose: Maintains high security and compliance standards, protecting the system against potential threats and ensuring adherence to regulatory requirements.

**Cultural Elements:**

- Overview: Foster a blameless culture focused on problem-solving and continuous improvement, rather than fault-finding.
- Purpose: Promotes an environment of innovation and learning, where SLIs serve as unbiased metrics to guide team efforts and enhance system performance.

**Notes:**

- When going into the release engineering phase, the application should be decoupled to enable various tests to be performed against each subsequent microservice or solution.
  - This not only will help determine if that area performs as intended, but as you transition into more system and integration engineering, you can observe how certain processes in one subsection impact the next.
  - This information is going to be very useful for troubleshooting, as you can now pinpoint issues rapidly, understand what a normal system should look like and understand how one component integrates with the next.
- Errors are bound to take place, determine what your SLO is for error rates and ensure your SLI is aligned to track that.
- Building the ability to observe the application with appropriate metrics and logs, building the application with clearly defined integrations between each component.
- When reviewing **release engineering** the following practices should be standardized:
  - Building
    - When developing, consistent builds should be used (ie. Pulling from specific, immutable, dependencies) to ensure that a consistent feature or product is being built.
      - This could be in the form of using build containers, package managers such as Maven, or local dependencies repositories.
      - Name packages after what component they support (ie. Frontend, backend, load balancing, etc.) (Google, 2017).
- During release engineering testing, these tests should test the anticipated behavior of the application or system. So, for instance, we are testing to validate that the feature or update being introduced into the application/ system does not negatively affect the performance or behavior of the intended unit (ie. CPU usage, network latency, internal system latency (system to database), etc.) (Kuefler, n.d.).
- Some follow-on items for deep dive research to expand on the framework, as it pertains to the integration of SRE practices:
  - Preparedness and disaster testing
    - Systems should behave as intended
    - Identify security gaps in the system proactively
    - Detailed requirements and design documents
      - Gather this information from the application or systems user base
      - Risk appetite!
    - Defense in depth
  - Postmortem culture
    - What occurred
    - Response effectiveness
    - After-action reporting
    - Remediation efforts
  - Automation and reduced operational overhead
  - Structured and rational decision making
  - Chaos Engineering methods

### Big Point to focus on for long-term SRE

- Principles
  - Embracing Risk
  - SLIs, SLOs, & SLAs
  - Eliminating TOIL
  - Logging and Monitoring Microservices
  - Release Engineering

- Practices
  - Practicality
  - Effectiveness
  - Managing Efficiency & Security Issues/ Incidents
  - Learning From Failure/ After Action Reporting
  - Tracking Outages (if a SLO is not met, the service is downgrading towards outage)
  - Reliability Testing (test to ensure intended behavior is met)
  - Addressing Cascading Issues (domino effect; one server is impacting sending the load down the line causing more downtime)

- Management
  - When addressing management, decision making is such an important aspect when determining when an action item is considered TOIL and when it is considered necessary. Various case studies in the GOOGLE SRE book highlight that slow methodical industries that have a higher risk impact may rely on the more manual side of things, whereas lower risk impact may rely on data-driven analysis.
  - Overall, understanding when is the right time to automate and orchestrate using data-driven analysis is critical to avoid a downtime impacting the businesses bottom-line or its users.

### Tools

Begimher. (2024). _Automated Security Helper._ GitHub. <https://github.com/awslabs/automated-security-helper>

Begimher. (2023). _My arsenal of aws security tools._ GitHub. <https://github.com/jusinoh/my-arsenal-of-aws-security-tools>

Begimher. (2022). _Devsecops._ GitHub. <https://github.com/begimher/DevSecOps>

Dastergon. (2022). _Awesome sre._ GitHub. <https://github.com/jusinoh/awesome-sre>

OpenScap. (n.d.). _Openscap: Audit, fix, be merry._ <https://www.open-scap.org/>

Tesauro, M. (n.d.). _API security tools._ OWASP. <https://owasp.org/www-community/api_security_tools#>

Wichers, D. (n.d.). _Free for open source application security tools._ OWASP. <https://owasp.org/www-community/Free_for_Open_Source_Application_Security_Tools>