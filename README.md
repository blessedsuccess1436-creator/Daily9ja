DAILY9JA — COMPLETE MASTER DEVELOPMENT PROMPT

1. PROJECT OVERVIEW

Build Daily9ja, a complete, production-oriented, mobile-first social earning platform that combines online activities, a rewards system, a wallet, peer-to-peer messaging, music streaming, social media, creator monetization, referrals, advertising integrations and an administrative control centre.

This must be a functional application with a real backend, persistent database, secure authentication, working business logic and properly connected features. Do not build a static demonstration, a frontend-only mockup or a collection of buttons that do nothing.

The platform should initially target mobile web browsers, especially Android devices, and support an installable Progressive Web App (PWA). Keep the architecture suitable for adding native Android and iOS applications in the future.

The name displayed throughout the platform must be Daily9ja.

Core product principles

- A clean, professional interface with a consistent design system.
- Responsive layouts that work on small Android screens, tablets and desktops.
- No horizontal scrolling on mobile.
- Use proper SVG icons, PNG assets and real interface components rather than replacing important graphics with emojis.
- Use loading indicators, empty states, success messages, error messages and confirmation dialogs.
- Every financial action must be backed by server-side logic.
- Every earning activity must have explicit eligibility rules and a funding source.
- Administrative controls must be enforced by the backend, not merely hidden in the frontend.
- Keep promotional credit, deposited money, pending rewards and verified earned cash separate.
- Do not show fake statistics, fake payment confirmations, fabricated users or simulated earnings as real data.

2. REQUIRED TECHNOLOGY AND ARCHITECTURE

Use the following as the initial implementation proposal.

Frontend

- React.
- TypeScript.
- Vite.
- Responsive CSS or a consistent component-based styling system.
- Progressive Web App support.
- Accessible forms, menus, dialogs, navigation and keyboard controls.
- Reusable components rather than duplicated screens.

Backend and infrastructure

Use Firebase Authentication for identity, Cloud Functions or another trusted server environment for protected business logic, and Firestore for application data and real-time features where appropriate.

Use protected object storage for profile images, posts, voice notes, video and other permitted media.

Before real-money launch, evaluate whether a transactional SQL database or dedicated financial ledger service should handle financial balances and transfers. Do not compromise ledger consistency just to use a single database technology.

Use environment variables and managed secrets for API credentials. Never expose secret keys, payment credentials, private signing keys or advertising tokens in frontend code.

Main backend services

Implement separate modules for:

1. Authentication and account onboarding.
2. User profiles and generated user IDs.
3. Wallet and financial ledger.
4. Deposits and payment reconciliation.
5. Withdrawals and payout processing.
6. Promotional credits and reward campaigns.
7. Tasks, referrals and earning activities.
8. Social posts, comments and engagement.
9. Private and group messaging.
10. End-to-end encryption and device-key management.
11. Voice and video call signalling.
12. Music playback and licensed media.
13. Advertising and advertiser campaigns.
14. Google Ads and Meta Ads integrations.
15. Notifications.
16. Moderation, reporting and anti-fraud.
17. Administration, permissions and audit logs.

All services must have documented interfaces and clear ownership of business rules.

---

3. EXACT SIGNUP AND ONBOARDING FLOW

This flow is mandatory. Do not send users directly from registration to the main dashboard.

Step 1: Authentication screen

When a visitor opens Daily9ja, display a clean authentication screen containing:

- Daily9ja logo and brand name.
- Email input.
- Password input.
- Sign In button.
- Continue with Google button.
- Forgot Password link.
- Create Account link.
- Terms of Service and Privacy Policy links.

The screen should be simple and professional. Do not overcrowd it with earning advertisements, wallet balances or unnecessary information.

Email registration must include appropriate email verification. Google registration must use the official Google authentication flow.

Step 2: Username creation

After successful email registration or Google authentication, route the user to a dedicated username setup page.

Display a heading such as:

Choose your Daily9ja username

Explain that the username will identify the user on their profile, posts, comments and chats.

Required behaviour:

- The user enters a username.
- Validate length, permitted characters and reserved words.
- Check username availability on the server.
- Normalize usernames consistently.
- Prevent two accounts from claiming the same username.
- Provide an availability indicator and useful validation errors.
- Allow a user to retry if the username is already taken.
- Save the username securely before proceeding.

Do not treat a Google display name as proof that the user has selected an available Daily9ja username.

The user must tap Next to continue.

Step 3: Unique Daily9ja ID generation page

After the user taps Next, open a separate full-page onboarding screen.

Display a message such as:

Creating your Daily9ja ID

Supporting text:

“We're preparing your unique account ID. Please wait a moment.”

Show a polished loading animation or progress indicator while the backend creates the user's permanent Daily9ja ID.

The ID must be generated on the server, not randomly invented by the frontend.

Requirements:

- Every account receives one permanent, unique Daily9ja ID.
- Enforce uniqueness with database constraints or a transaction-safe allocation process.
- Use a secure collision-handling strategy.
- Prevent users from selecting or editing another user's ID.
- Make ID generation idempotent so refreshing the page does not create multiple IDs.
- Save the ID before continuing to profile setup.
- If generation fails, display a retry option without creating duplicate accounts.
- If the ID was already created, retrieve and display the existing ID instead of generating another.

When successful, display the generated ID clearly and show a Next button.

Do not leave users on an endless loading screen.

Step 4: Profile picture and personal details

After ID generation, open the profile setup page.

Display:

Set up your profile

Allow the user to:

- Upload a profile picture in PNG format.
- Preview the selected picture.
- Crop or position it before saving.
- Remove or replace the picture.
- Enter a display name.
- Add an optional short bio.
- Set other non-sensitive profile information that Daily9ja genuinely needs.

PNG upload requirements

- Accept PNG profile pictures and validate their actual file format, not just the extension.
- Set configurable file-size and image-dimension limits.
- Re-encode or sanitize uploaded images using a trusted image-processing library.
- Generate appropriately sized profile thumbnails.
- Store images in protected object storage with controlled public delivery.
- Do not trust client-supplied filenames or MIME types.
- Reject malformed or excessively large files.
- Provide a default profile avatar if the user skips uploading a picture.

Allow the user to continue without a profile picture unless it is required for a specific verified activity.

Step 5: Additional account setup popup

After the profile details have been saved, display a setup popup or dedicated step inviting the user to complete their withdrawal setup.

The popup should offer two choices:

Set Up Now

Skip for Now

Allow the user to skip this step and continue to the dashboard.

The setup flow may request:

- Bank account details needed for future payouts.
- Bank account verification through an appropriate provider.
- A six-digit transaction PIN.
- PIN confirmation.
- Any required disclosures or consent.

The PIN must be created and verified on the server using a suitable password-hashing algorithm. Never store the PIN as plaintext or in browser storage.

If the user skips setup:

- Do not block dashboard access.
- Show a clear setup reminder where appropriate.
- Do not permit withdrawals until the required bank details and PIN are configured.
- Allow the user to complete setup later from Wallet Settings.
- Do not repeatedly show an intrusive popup after every page navigation.

Do not ask for bank information or a transaction PIN merely to authenticate the user's identity.

Step 6: Enter the dashboard

After the profile setup step is completed or skipped, take the user to the main Daily9ja dashboard.

The dashboard should display:

- Welcome message.
- Username.
- Permanent Daily9ja ID.
- Profile picture.
- Account verification status where applicable.
- Promotional credit balance.
- Deposited balance and eligible earned-cash balance as separate figures.
- Pending rewards.
- Quick actions for wallet, activities, referrals, posts, music and messages.
- Recent transactions and earning activity.
- Notifications and onboarding reminders.

The dashboard must fetch real information from the backend. Do not use fixed sample balances as if they belong to a real user.

Step 7: Issue the ₦2,000 welcome promotion

Only after successful completion of the onboarding flow and entry into the dashboard should the system issue the eligible user's ₦2,000 welcome promotional credit.

This must happen through a server-side operation that can safely be retried without issuing the bonus twice.

Requirements:

- Credit the promotional-credit ledger, not the cash-withdrawable balance.
- Use a unique welcome-bonus grant identifier.
- Enforce one eligible grant per account and the published promotion rules.
- Record the grant date, amount, campaign ID and status.
- Display a welcome notification after the credit has been successfully recorded.
- Refresh the promotional balance from the backend.
- If the user refreshes the page or signs in again, do not issue a second bonus.
- If the grant fails, retry safely and show an accurate status.
- Do not claim that the bonus was credited before the transaction succeeds.

Suggested welcome message:

“Welcome to Daily9ja! Your ₦2,000 promotional credit is now available for eligible Daily9ja activities. Promotional credit cannot be directly withdrawn or transferred.”

The welcome credit must not be represented as cash that the user can immediately withdraw.

---

4. USER ACCOUNT AND PROFILE SYSTEM

Each user must have a secure, persistent account containing:

- Internal immutable user ID.
- Public Daily9ja ID.
- Unique username.
- Display name.
- Profile picture URL or media reference.
- Optional bio.
- Account creation timestamp.
- Email verification status.
- Authentication provider information.
- Account status.
- Verification badge status.
- Privacy preferences.
- Notification preferences.
- Onboarding completion state.
- Referral attribution where applicable.
- Device and security-session metadata.

Never expose authentication tokens, private contact details, bank details, internal fraud scores or sensitive security metadata on public profiles.

Provide account settings for changing profile details, managing sessions, changing passwords, resetting the transaction PIN and requesting account deletion subject to applicable legal retention requirements.

Account linking

Email/password and Google authentication must connect to the same account only through a secure identity-linking process.

Do not merge accounts merely because they have similar usernames or display names.

Require proof of ownership when linking a new authentication method to an existing account.

---

5. BLUE VERIFICATION BADGE

Create an official blue verification badge for eligible users.

The badge must appear beside the user's display name in supported locations, including:

- Profile pages.
- Social posts.
- Comments.
- Search results.
- Chat profile previews where appropriate.

Admin verification tools

Authorized administrators must be able to:

- Search for users.
- Review verification requests.
- Examine appropriate supporting evidence.
- Approve or reject verification.
- Assign or remove the blue badge.
- Record a reason for the decision.
- Record who made the change and when.
- Notify the user of the outcome.

Define published eligibility criteria so the badge has a consistent meaning.

Do not allow ordinary users to assign badges to themselves. All verification changes must be authorized by the backend and written to an audit log.

Use proper SVG icon assets for the badge. Do not rely on an emoji to represent official verification.

---

6. DAILY9JA WALLET AND FINANCIAL LEDGER

Build a secure wallet with separate accounting categories.

Required categories

1. Promotional credit.
2. Pending rewards.
3. Verified earned cash.
4. Deposited funds.
5. Reserved funds for withdrawals or transfers.
6. Reversed or refunded transactions where applicable.

Do not combine these categories into a single editable balance.

Ledger rules

- All financial changes must be performed by trusted backend services.
- Each operation must produce auditable ledger entries.
- Entries must not be silently deleted or overwritten.
- Corrections should use properly authorized reversing entries.
- Use integer minor currency units, such as kobo, rather than floating-point arithmetic for NGN amounts.
- Use idempotency keys to prevent duplicate credits, transfers and payouts.
- Reconcile internal ledger records with external payment-provider records.
- Use atomic transactions or a suitable ledger service to maintain consistency.
- Prevent negative balances unless an explicitly designed and authorized accounting process permits them.

The user interface may display balances, but it must never be the authority that determines a user's funds.

Wallet pages

Create:

- Wallet overview.
- Deposit.
- Withdraw.
- Send Money.
- Receive Money.
- Transaction history.
- Reward history.
- Saved payout accounts.
- PIN setup and recovery.
- Transaction details.
- Payment and transfer status pages.

Each transaction must have a unique reference, amount, date, status and appropriate description.

---

7. USER-TO-USER CASH TRANSFERS

Users may send verified, available earned cash to another eligible Daily9ja user.

Promotional credit and pending rewards must never be transferable.

For Version 1.0, implement a controlled and auditable transfer workflow, enabled only after the platform's applicable financial and provider requirements have been satisfied.

Transfer process

1. The sender selects Send Money.
2. The sender enters the recipient's Daily9ja ID or another supported recipient identifier.
3. The system displays the verified recipient profile for confirmation.
4. The sender enters the amount.
5. The system displays any applicable fee and the final amount.
6. The sender confirms the transaction with the six-digit transaction PIN.
7. The backend checks sender eligibility, recipient status, available earned cash, transfer limits and fraud controls.
8. The backend executes the debit and credit atomically.
9. The system generates a transfer reference and receipt.
10. Both users receive appropriate transaction notifications.

Mandatory controls

- Prevent sending money to oneself.
- Prevent sending more than the available eligible balance.
- Prevent duplicate transfers.
- Apply configurable transfer limits.
- Apply risk-based checks for unusual transfer activity.
- Support clear failure and reversal procedures.
- Keep a complete audit trail.
- Do not let promotional credit or pending rewards enter the transferable balance.
- Do not allow a transfer to be marked successful based only on a frontend response.

Deposited funds must remain a distinct category and must not automatically become transferable earned cash. Their treatment must follow the approved wallet model and applicable requirements.

---

8. DEPOSITS, WITHDRAWALS AND PAYMENT GATEWAY

Paystack

Use Paystack as the preferred gateway, subject to merchant approval and confirmation that the intended transactions are supported.

Integrate the appropriate approved payment methods and payout features.

Deposit flow

1. User enters an amount.
2. Backend validates the amount and user eligibility.
3. Backend creates the payment request with the provider.
4. User completes the provider's checkout process.
5. Backend verifies the payment through authenticated provider records or signed webhooks.
6. The backend checks the amount, currency, payment reference and transaction status.
7. Only a verified successful payment can be credited.
8. The internal ledger records the credit once.
9. The user sees an accurate status and receipt.

Never credit funds merely because the browser returns to a success URL.

Manual bank-transfer fallback

Provide a manual-transfer option when appropriate.

- Display the correct designated receiving-account details.
- Generate a unique payment reference where supported.
- Let users submit a reference for reconciliation.
- Match transfers against actual receiving-account or provider records.
- Allow pending, verified, rejected and expired statuses.
- Do not accept a screenshot alone as proof that money arrived.
- Do not credit a deposit until it has been independently verified.

Withdrawal process

1. User enters the withdrawal amount.
2. System displays the eligible balance, fee and final payout amount.
3. User selects a verified bank account.
4. User confirms with the six-digit transaction PIN.
5. Backend validates available balance, limits, account status and risk checks.
6. Funds are reserved atomically.
7. A withdrawal request is created.
8. The payout is submitted through an approved provider or reviewed through a properly controlled process.
9. The status changes only when supported by authoritative payout information.
10. Failed payouts release reserved funds safely and exactly once.

Possible statuses include pending, processing, paid, failed, rejected and cancelled where cancellation is supported.

Withdrawal fees

If withdrawal fees are enabled, configure and disclose them before confirmation. Do not introduce hidden charges or require users to pay an invented fee to unlock nonexistent earnings.

---

9. TRANSACTION PIN AND ACCOUNT SECURITY

Implement a six-digit transaction PIN for withdrawals and other sensitive financial actions.

Requirements:

- Users create and confirm their PIN.
- Hash PINs on the server using an appropriate password-hashing approach.
- Never store the PIN in plaintext.
- Never expose it to administrators.
- Rate-limit failed attempts.
- Apply temporary lockouts or step-up verification after suspicious attempts.
- Provide a secure reset process.
- Notify users of relevant security changes.
- Protect against replay attacks and repeated submissions.
- Do not store PINs in local storage, session storage, URLs or analytics logs.

Use secure authentication sessions, email verification, account recovery, server-side authorization and appropriate protection against common web vulnerabilities.

Require stronger authentication for sensitive administrator actions.

---

10. CENTRAL ACTIVITY AND REWARD ENGINE

Build a configurable activity engine so administrators can add, edit, pause and retire earning activities without rewriting the entire application.

Every activity should have:

- Activity ID.
- Activity type.
- Name and instructions.
- Reward amount or reward calculation rule.
- Eligibility requirements.
- Start and end dates.
- Daily and per-user limits.
- Total campaign budget.
- Required evidence or completion event.
- Verification method.
- Review status.
- Funding source.
- Reward issuance status.
- Fraud-prevention rules.

Do not allow arbitrary executable code to be entered as an activity configuration.

Initial activity catalogue

A. Daily engagement

- Daily check-in.
- Streak milestones.
- Profile-completion challenges.
- Knowledge quizzes.
- Educational challenges.
- Limited-time promotional events.

B. Tasks

- Complete approved learning modules.
- Submit eligible feedback.
- Participate in approved surveys.
- Complete sponsored tasks.
- Submit content for review.
- Complete campaigns with measurable completion criteria.

C. Referrals

- Unique referral links.
- Unique referral codes.
- Registration tracking.
- Qualification milestones.
- Reward approval.
- Referral history.
- Configurable referral caps and campaign budgets.

A referral must not automatically become payable just because someone clicks a link or creates an account.

D. Social and creator activities

- Publish eligible original content.
- Participate in sponsored content campaigns.
- Complete approved creator challenges.
- Join moderated community events.
- Participate in funded brand partnerships.

Do not automatically pay unlimited rewards for likes, views, followers or comments. Those actions are vulnerable to manipulation and may violate advertising-platform policies.

E. Business activities

- Sponsored product discovery.
- Approved feedback campaigns.
- Brand partnership tasks.
- Advertiser-funded content.
- Eligible campaign participation.

F. Future activities

Prepare extensible activity types for later releases:

- Music-related features where licensing and business rules allow.
- Virtual mining and upgrade mechanics.
- Collectibles and NFT-related features.
- Ludo and other games.
- Other competitions or reward campaigns.

Do not activate real-money gaming, staking, investment or trading products until their funding model, technical controls and applicable requirements have been reviewed.

---

11. ₦2,000 WELCOME PROMOTIONAL CREDIT

The welcome promotion must be configurable by an authorized administrator.

Default amount: ₦2,000 promotional credit.

Requirements:

- Award only to eligible new accounts.
- Grant only after the specified onboarding flow is complete and the dashboard has been entered.
- Do not issue the grant twice.
- Record each grant in the promotional-credit ledger.
- Show its conditions and restrictions clearly.
- Prevent direct cash withdrawal.
- Prevent peer-to-peer transfer.
- Prevent conversion into earned cash unless a separately reviewed and explicitly designed promotion permits it.
- Allow the admin to pause the campaign or change the amount for future eligible accounts.
- Do not retroactively alter an existing grant without a documented, authorized correction process.

Until an eligible activity exists, show the promotional balance as restricted promotional credit. Do not imply that users can spend it on activities that have not been implemented.

---

12. REFERRAL SYSTEM AND ANTI-FRAUD

Create a referral dashboard with:

- Referral link.
- Referral code.
- Number of registrations.
- Number of qualified referrals.
- Pending rewards.
- Approved rewards.
- Rejected claims and explanations where appropriate.
- Campaign limits.
- Referral history.

Anti-abuse requirements

- Prevent self-referral.
- Prevent duplicate referral reward issuance.
- Require qualifying activity before rewards are payable.
- Detect suspicious account clusters and repeated claim patterns.
- Apply rate limits to registration and reward claims.
- Flag unusually high signup rates from an IP address.
- Use privacy-conscious device-risk signals.
- Use VPN and proxy intelligence where available.
- Apply additional checks to high-risk accounts.
- Support human review and appeals.

Do not automatically ban every account sharing one IP address. Mobile networks, homes, schools, offices and public Wi-Fi can legitimately share IP addresses.

VPN detection is probabilistic. Treat it as a risk signal, not proof of wrongdoing.

Do not rely on browser fingerprinting as a guaranteed way to identify a unique human. Minimize personal-data collection and provide appropriate privacy disclosures.

---

13. SOCIAL FEED AND CREATOR PROFILES

Create a full social feed with:

- User profiles.
- Posts containing text, photos, videos and permitted audio.
- Likes and comments.
- Sharing and saving.
- Following and unfollowing.
- Content visibility settings.
- Post editing and deletion.
- Notifications.
- Search and discovery.
- Hashtags or topic tags where useful.
- Reporting and blocking.
- Moderation tools.
- Creator analytics.

Use proper image and video assets. Build clean post cards and responsive media viewers rather than a template filled with emojis.

Content controls

- Validate and scan uploaded files.
- Apply file-size and media-duration limits.
- Provide reporting and moderation workflows.
- Prevent spam, impersonation and malicious links.
- Enforce copyright and content rules.
- Provide privacy controls for profiles and posts.

Do not make private content public through misconfigured storage permissions.

---

14. CREATOR MONETIZATION AND ADVERTISING

Create a connected advertising system for users, businesses and Daily9ja administrators.

A. Daily9ja-sponsored promotions

Allow eligible users and businesses to:

- Create sponsored posts.
- Select supported campaign goals.
- Set campaign budgets.
- Choose permitted audience options.
- Set campaign start and end dates.
- Submit campaigns for moderation.
- Track delivery and performance.
- Pause or cancel campaigns according to the rules.

Display sponsored content clearly. Prevent misleading claims, scams, prohibited products and unauthorized advertising.

B. Advertiser-funded reward campaigns

Advertisers may fund eligible activities such as approved feedback or sponsored content.

The system must track:

- Advertiser identity.
- Campaign budget.
- Reserved and spent amounts.
- Approved actions.
- Fraud checks.
- Reward obligations.
- Remaining budget.
- Campaign status.
- Reconciliation records.

Do not promise advertisers that every view or click is genuine. Use appropriate measurement and invalid-traffic controls.

Do not incentivize fake ad clicks or artificial impressions. Follow the policies of any advertising network used.

C. Google AdSense

Provide an integration plan for displaying approved publisher advertisements on Daily9ja.

- Require website approval and compliance with the applicable publisher policies.
- Add approved ad placements only where permitted.
- Use the appropriate publisher-provided code and configuration.
- Respect consent and privacy requirements.
- Do not generate fake clicks or incentivized interactions.
- Do not promise users a reward for clicking ordinary AdSense advertisements.
- Do not fabricate publisher revenue when no revenue data is available.

D. Google Ads API

Provide an official integration pathway for eligible advertisers to connect Google Ads accounts.

Potential capabilities, subject to API permissions and approval:

- Account connection using OAuth.
- Authorized account selection.
- Supported campaign creation and management.
- Campaign status.
- Budget management within authorized limits.
- Performance reporting.
- Error handling and token revocation.

Use official Google Ads API documentation and supported SDKs. Request only the permissions needed for each feature.

E. Meta Marketing API

Provide an official integration pathway for eligible users to connect Facebook and Instagram advertising accounts.

Potential capabilities, subject to Meta's current requirements:

- Authorized account connection.
- Supported campaign management.
- Campaign reporting.
- Budget and status information.
- Access-token lifecycle management.
- Permission and app-review status.

Use the official Meta Marketing API and approved authentication flows.

Do not assume that API access is available immediately. Display connection status and useful setup instructions if an account or permission is awaiting approval.

F. Advertising integration centre

Build an admin and advertiser interface showing:

- Integration provider.
- Connection status.
- Authorized account.
- Granted permissions.
- Token expiry or reauthorization status where available.
- Campaign list.
- Budget and performance data.
- Errors and warnings.
- Disconnect and revoke-access options.

Store refresh tokens and secrets only in protected backend storage. Never embed them in the frontend or expose them in logs.

Do not promise that a browser extension will unlock features that the official API does not permit.

---

15. MUSIC PLAYER AND BACKGROUND PLAYBACK

Build a proper music experience with:

- Search.
- Play and pause.
- Next and previous track.
- Shuffle and repeat.
- Playlists.
- Favourites.
- Listening history.
- Playback progress.
- Volume control where supported.
- Queue management.
- Artist and track metadata.
- Audio quality appropriate to the available source.
- Responsive mini-player.
- Persistent player state across supported navigation.
- Media-session metadata and compatible device controls.

Background playback

Design the web app as a PWA and use supported browser media capabilities so playback can continue when the user switches tabs or minimizes the browser where the operating system and browser allow it.

Test actual behaviour on Android Chrome, iPhone Safari and installed PWAs.

Do not promise uninterrupted playback on every device. Browser and operating-system restrictions may suspend audio.

Music licensing

Use authorized music catalogues, properly licensed streams or user-uploaded material that the user has permission to distribute.

Do not scrape commercial streaming services or bypass digital-rights controls.

Do not automatically pay users simply for leaving music playing. Any music-related earning campaign must have a lawful, measurable and properly funded model.

---

16. PRIVATE CHAT, GROUPS AND MESSAGING

Build a real-time messaging system with:

- One-to-one conversations.
- Group conversations.
- Text messages.
- Photos and videos.
- File attachments.
- Voice notes.
- Message replies.
- Message reactions.
- Message editing and deletion rules.
- Read receipts.
- Delivery status.
- Typing indicators.
- Online and last-seen settings.
- Search where compatible with encryption.
- Pinned messages.
- Message forwarding controls.
- Block and report.
- Disappearing messages.
- View-once media.
- Push and in-app notifications.

Include group membership management, invitation controls, administrator roles and moderation tools.

End-to-end encryption

End-to-end encryption is a core architectural requirement for private chats and calls.

Use established, independently reviewed cryptographic protocols and libraries. Do not invent a custom encryption algorithm.

The design must address:

- Device identity keys.
- Session-key establishment.
- Message encryption and authentication.
- Forward secrecy where supported.
- Secure key storage on devices.
- Device linking and revocation.
- Group key management.
- Key rotation.
- New-device verification.
- Account recovery.
- Encrypted media uploads.
- Encrypted backup options.
- Security notifications when identity keys change.

Private message content and media must be encrypted on the sender's device and decrypted only on authorized recipient devices.

The server may store encrypted payloads and the metadata necessary for delivery, subject to the privacy design. It must not claim to provide end-to-end encryption if the backend can read the supposedly encrypted content.

Do not claim that E2EE hides all metadata. Explain what information the service still needs to process.

View-once media

Implement expiration and one-time access rules where technically possible.

Explain to users that screenshots, external cameras and compromised devices cannot be reliably prevented in every situation.

Abuse reporting

Provide a reporting workflow compatible with the encryption design. Make clear when a user voluntarily submits message content or other evidence for review.

Do not secretly bypass E2EE to read users' private messages.

---

17. VOICE AND VIDEO CALLING

Implement voice and video calls using WebRTC or an appropriate established real-time communications service.

Features:

- One-to-one voice calls.
- One-to-one video calls.
- Incoming call screen.
- Accept and decline.
- Mute and unmute.
- Camera on and off.
- Speaker and microphone controls where supported.
- Call duration.
- Missed-call notifications.
- Call history.
- Permission handling.
- Connection-quality indicators.
- Call termination and reconnection handling.

Use authenticated signalling and end-to-end media protection.

Handle camera and microphone permissions carefully. Do not activate them without the appropriate user action and consent.

Consider group calls as a later milestone if they materially increase complexity.

Test network interruptions, permissions, browser compatibility and mobile data usage.

---

18. NOTIFICATIONS

Build in-app and supported push notifications for:

- Welcome promotion.
- Reward approvals and rejections.
- Referral progress.
- Deposits and withdrawals.
- Incoming transfers.
- New messages.
- Incoming calls and missed calls where supported.
- Comments and social interactions.
- Verification decisions.
- Advertising campaign updates.
- Security alerts.

Let users configure notification preferences.

Do not expose private message contents on lock screens unless the user explicitly enables message previews.

---

19. ADMIN DASHBOARD AND PERMISSIONS

Create a protected administration area that is accessible only to authorized staff.

User management

- Search users by Daily9ja ID, username and supported account identifiers.
- View account status.
- Restrict or suspend accounts with recorded reasons.
- Review verification requests.
- Assign or remove verification badges.
- Review reports and appeals.
- Review suspicious activity.

Wallet and payment management

- View deposits and their verified statuses.
- Review manual-transfer reconciliation.
- View withdrawal requests.
- Review payout status.
- Review transfers and ledger entries.
- View reward liabilities and campaign funding.
- Apply controlled corrections through audited transactions.

Administrators must not be able to silently edit financial balances.

Reward management

- Create and configure reward campaigns.
- Set activity eligibility.
- Set reward amounts.
- Set daily, weekly and campaign limits.
- Define qualification conditions.
- Pause or close campaigns.
- Review pending claims.
- View budget usage.
- Audit reward issuance.

Advertising management

- Review advertiser accounts.
- Review campaigns and sponsored posts.
- Manage platform-owned placements.
- View approved integrations and permissions.
- Review campaign budgets and reported results.
- Pause prohibited or suspicious campaigns.

Security and moderation

- Manage roles and permissions.
- Review audit logs.
- Investigate reports.
- Revoke compromised sessions.
- Configure risk thresholds.
- Manage support cases and appeals.
- Record administrative reasons for important actions.

Use least-privilege permissions. Sensitive operations should require appropriate reauthentication or stronger authentication.

---

20. USER EXPERIENCE AND DESIGN SYSTEM

Create a coherent, polished interface.

Visual direction

- Clean and modern.
- Strong visual hierarchy.
- Consistent spacing and typography.
- Clear navigation.
- Professional cards and data tables.
- Consistent SVG icons.
- Properly sized PNG and other approved media.
- Responsive layouts without horizontal overflow.
- Clear loading, empty, disabled and error states.
- Dark and light themes if practical.
- Accessible contrast and touch targets.

Do not use a phone mockup inside the website. The website itself must be responsive to the user's actual browser viewport.

Suggested main navigation

Provide a mobile-friendly navigation system with access to:

- Home.
- Earn.
- Social.
- Music.
- Messages.
- Wallet.
- Profile and Settings.

Use a suitable bottom navigation on small screens and a responsive navigation pattern on larger screens.

Do not overcrowd the first screen with every feature. Organize activities into clear categories and provide search or filtering when the activity catalogue grows.

---

21. DATA MODEL AND DATABASE DESIGN

Design normalized or appropriately structured records for the following entities:

- Users.
- User authentication identities.
- Usernames and generated Daily9ja IDs.
- Profiles.
- Verification requests and badge history.
- Devices and sessions.
- Wallet accounts.
- Ledger entries.
- Deposits.
- Withdrawals.
- Peer-to-peer transfers.
- Payout accounts.
- Transaction PIN security metadata.
- Reward campaigns.
- Reward claims.
- Promotional-credit grants.
- Referrals.
- Tasks.
- Social posts.
- Comments and reactions.
- Followers and following.
- Media objects.
- Conversations.
- Conversation membership.
- Encrypted messages.
- Device cryptographic identities.
- Group encryption metadata.
- Call signalling records.
- Notifications.
- Advertisers.
- Advertising campaigns.
- Advertising integrations.
- Provider connection metadata.
- Moderation reports.
- Support tickets.
- Admin roles.
- Admin audit logs.

Use stable internal identifiers, timestamps, defined status transitions and appropriate indexes.

Keep sensitive records separate from public profile data.

Enforce ownership and authorization at the server and database-rule level. Never rely only on frontend route protection.

---

22. SECURITY, PRIVACY AND COMPLIANCE

Implement security throughout development rather than adding it at the end.

Required controls include:

- Server-side authorization.
- Secure authentication and account recovery.
- Input validation and output encoding.
- Protection against common web vulnerabilities.
- Rate limiting.
- Upload validation and scanning.
- Secure secret storage.
- Payment-webhook signature validation.
- Replay and duplicate-request protection.
- Atomic financial operations.
- Audit logs.
- Data minimization.
- Appropriate retention and deletion rules.
- Encrypted transport.
- Secure key management.
- Backup and disaster recovery.
- Monitoring and incident response.
- Appropriate privacy disclosures and user consent.

Review the applicable Nigerian and other relevant laws before enabling real-money wallet services, payouts, paid advertising, cash-convertible digital items, real-money games or investment-related products.

Do not assume that a payment gateway's merchant approval automatically authorizes every possible wallet, gaming or financial product.

---

23. IMPLEMENTATION AND RELEASE PLAN

Build the platform incrementally. Do not try to activate every complex feature in the first release.

Release 1.0 — Core foundation

Implement:

- Authentication.
- Username setup.
- Unique Daily9ja ID generation.
- PNG profile upload.
- Optional bank and PIN setup popup.
- Dashboard.
- ₦2,000 promotional-credit grant.
- Wallet data model and ledger.
- Admin authentication and roles.
- Payment integration in test mode.
- Manual-transfer reconciliation workflow.
- Withdrawal requests.
- Security logging and foundational anti-fraud controls.

Do not enable real payouts until the relevant provider setup, reconciliation, security testing and applicable compliance checks are complete.

Release 1.1 — Earning and referrals

Implement:

- Task engine.
- Daily check-ins.
- Referral system.
- Admin reward configuration.
- Campaign budgets and eligibility.
- Reward approval and rejection.
- Fraud review.

Release 1.2 — Social and creator tools

Implement:

- Profiles.
- Social feed.
- Posts and comments.
- Media uploads.
- Follows.
- Notifications.
- Creator dashboards.
- Sponsored campaigns.
- Moderation.

Release 1.3 — Messaging and money transfers

Implement:

- Peer-to-peer earned-cash transfers, subject to the approved financial model.
- Private and group chat.
- Encrypted text and media.
- Voice notes.
- Device key management.
- Delivery states and notifications.

Release 1.4 — Music and calling

Implement:

- Licensed music playback.
- Playlists.
- Background playback where supported.
- Voice and video calls.
- View-once media.
- Disappearing messages.

Release 1.5 and later — Advertising integrations and expansion

Implement and expand:

- Google AdSense integration after publisher approval.
- Google Ads API integration subject to access and authorization.
- Meta Marketing API integration subject to permissions and review.
- Advertiser accounts and campaign management.
- Additional activities.
- Virtual mining and upgrades.
- Collectibles and NFT features.
- Games and other reviewed expansion features.

The release order may be adjusted when dependencies require it. Do not present an unimplemented feature as complete.

---

24. TESTING AND ACCEPTANCE CRITERIA

Before declaring any release complete, test its actual behaviour.

Authentication and onboarding

- Email registration works.
- Google sign-in works.
- Username availability is enforced.
- IDs are unique and persistent.
- Refreshing the ID-generation page does not create another ID.
- PNG uploads are validated.
- Skipping withdrawal setup works.
- Welcome credit is issued exactly once after the required onboarding flow.

Wallet and payments

- Duplicate payment notifications cannot issue duplicate credits.
- Unverified payments cannot increase balances.
- Concurrent withdrawals cannot overspend a balance.
- Transfers debit and credit both accounts correctly.
- Failed operations do not leave inconsistent balances.
- Promotional credit and pending rewards cannot be transferred.
- Failed payouts release reserved funds correctly.
- Every transaction has an auditable reference.

Rewards and referrals

- Campaign limits are enforced.
- Duplicate claims are rejected.
- Referral abuse is detected appropriately.
- Paused campaigns cannot issue new rewards.
- Rewards are not payable beyond approved funding.

Social and communications

- Users can publish and moderate permitted content.
- Unauthorized users cannot read private content.
- Encrypted messages are not stored as readable plaintext on the server.
- Device revocation and key changes are handled correctly.
- Call permissions and connection failures are handled safely.
- View-once limitations are explained accurately.

Administration and advertising

- Ordinary users cannot access admin functions.
- Every privileged change is audited.
- API credentials are not exposed.
- Advertising accounts require authorization.
- Missing provider permissions are handled gracefully.
- Campaign spending is limited by approved budgets.

Mobile experience

- No horizontal scrolling on supported phone sizes.
- All primary actions work with touch.
- Forms display readable validation messages.
- Loading and error states are useful.
- Music playback is tested across supported browsers.
- Unsupported features fail gracefully rather than pretending to work.

---

25. REQUIRED DEVELOPMENT WORKFLOW

Before writing substantial code:

1. Inspect the existing repository and identify the current framework, backend and implemented features.
2. Preserve working functionality unless there is a clear reason to change it.
3. Create a technical plan and dependency map.
4. Define the database schema and authorization model.
5. Identify payment, messaging, music and advertising provider requirements.
6. Implement one release at a time.
7. Add automated tests for critical business logic.
8. Run type checks, linting, tests and production builds.
9. Fix errors before reporting completion.
10. Document environment variables, setup instructions, migrations, provider configuration and deployment.

If a required provider account, credential, approval or API capability is missing, create a clear integration boundary and explain what is needed. Do not fabricate successful API connections.

Do not hardcode secret keys, payment outcomes, balances, administrator identities or fake provider responses into production functionality.

Provide clear completion reports that distinguish implemented features, tested features, externally configured features and features still pending approval.

---

FINAL PRODUCT REQUIREMENT

The final Daily9ja product must be a connected platform rather than unrelated screens.

The authentication and onboarding flow must work exactly as specified. Users must receive their permanent Daily9ja ID, be able to upload a PNG profile picture, skip optional withdrawal setup, enter the dashboard and receive their eligible ₦2,000 promotional credit exactly once.

The wallet must use a trustworthy financial ledger. The earning system must be configurable by administrators. The referral system must resist abuse. The social platform must provide appropriate privacy and moderation. Music must use authorized sources. Private chats and calls must be designed around genuine end-to-end encryption. Advertising integrations must use official provider APIs and respect their permissions and policies.

Build a secure, maintainable foundation first, then add the larger Daily9ja ecosystem in tested releases. Never sacrifice financial integrity, user privacy or real functionality just to make the interface appear complete.
