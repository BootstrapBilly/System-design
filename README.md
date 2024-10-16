# System-design
A place to store my thoughts when designing a globally distributed high scale e-commerce system

## Stage 1: Authentication

Authentication is the gateway to any successful large-scale, high-traffic e-commerce platform. It must handle hundreds of thousands of users seamlessly, safeguard their data, and ensure a smooth, secure experience.

### Considerations

#### Scalability
- **High Concurrent Requests**: Handle thousands of users simultaneously during big sales events.
- **Horizontal Scalability**: Scale easily during peak times by adding more servers.

#### Availability
- **Multi-Region Deployment**: Serve users globally with minimal latency.
- **Redundancy & Failover**: Automatic switchovers to keep the system running smoothly during failures.

#### Security
- **Multi-Factor Authentication (MFA)**: Add layers of security for critical user accounts.
- **Risk-Based Authentication**: Dynamic security based on user behavior, device, and location.
- **Token-Based Access**: Issue and verify tokens, ensuring stateless, secure interactions.
- **Bot/DDoS Protection**: Rate limiting and CAPTCHAs to fend off attacks.

#### Defense Against Malicious Users
- **Password Spray & Replay Attacks**: Detect and block repeated or recycled login attempts.
- **MITM, Phishing, and Session Hijacking**: SSL encryption, certificate pinning, and user prompts for anomalies.
- **CSRF & Account Enumeration**: CSRF tokens, generic error messages, and rate limiting to prevent abuse.
- **DDoS, Password Reset Abuse, Fake Accounts**: Rate limiting, CAPTCHA, and user alerts for strange activity.

#### Session Management
- **Token Refresh**: Stay logged in without re-authenticating.
- **Token Revocation**: Instantly invalidate compromised tokens.
- **Secure Token Storage**: Keep tokens safe using HttpOnly cookies or secure mobile storage.
- **Session Control**: Users can manage their active sessions and log out from others.
- **Privilege-Based Token Lifetimes**: Shorter lifetimes for higher privilege tokens (e.g., admin).

#### Performance
- **Low Latency**: Quick responses during logins, even during peak traffic.

#### Observability and Monitoring
- **Authentication Logs & Audit Trails**: Log every login attempt for compliance and analysis.
- **Anomaly Detection & Alerts**: Track and alert unusual login behaviors.

#### User Experience
- **Passwordless Magic Links**: Quick access without remembering passwords.
- **Social Logins**: One-click logins using Google, Facebook, etc.
- **Progressive Profiling**: Collect only minimal data upfront; gather more as needed.

#### Backup & Disaster Recovery
- **Restorable Sessions**: Regularly backup, and be able to recover session data seamlessly during disruptions.

#### Compliance
- **GDPR Compliance**: Full account deletion capability.
- **Minimal Information Collection**: Respect privacy, collect only what’s needed.

### What Identity Provider Should Be Used?

To handle up to 50,000 concurrent users without being limited by budget constraints, **Keycloak** is the best choice.

It's open-source, offers extensive features, requires self-managed infrastructure, and has no monthly active user limits, keeping costs low compared to managed options. While options such as **Auth0** provide more functionality and scaling, costs could extend into the thousands with the level of traffic we are expecting.

<img width="837" alt="image" src="https://github.com/user-attachments/assets/682a0699-30b4-4a8c-976a-6a5e99fa5518">

### Thinking about infrastructure
![image](https://github.com/user-attachments/assets/7cc9b679-556a-4433-851f-14c6420cf9f9)


