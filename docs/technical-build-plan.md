# WorkLinkApp Technical Build Plan

## 1. Folder & File Structure

```text
WorkLinkApp/
├─ app/
│  ├─ _layout.tsx                     # Root Expo Router layout, providers, auth gate
│  ├─ index.tsx                       # App entry / splash routing
│  ├─ (public)/
│  │  ├─ welcome.tsx
│  │  ├─ login.tsx
│  │  ├─ register/
│  │  │  ├─ role.tsx
│  │  │  ├─ account.tsx
│  │  │  ├─ verify-id.tsx
│  │  │  ├─ upload-id.tsx
│  │  │  ├─ profile-photo.tsx
│  │  │  ├─ worker-details.tsx
│  │  │  ├─ employer-details.tsx
│  │  │  └─ subscription-info.tsx
│  │  ├─ forgot-password.tsx
│  │  └─ legal/
│  │     ├─ privacy-policy.tsx
│  │     └─ terms.tsx
│  ├─ (worker)/
│  │  ├─ _layout.tsx                  # Tabs layout
│  │  ├─ home.tsx
│  │  ├─ jobs/
│  │  │  ├─ index.tsx
│  │  │  ├─ map.tsx
│  │  │  ├─ [jobId].tsx
│  │  │  └─ filters.tsx
│  │  ├─ messages/
│  │  │  ├─ index.tsx
│  │  │  └─ [threadId].tsx
│  │  ├─ profile/
│  │  │  ├─ index.tsx
│  │  │  ├─ edit.tsx
│  │  │  └─ verification-status.tsx
│  │  ├─ saved-jobs.tsx
│  │  └─ notifications.tsx
│  ├─ (employer)/
│  │  ├─ _layout.tsx                  # Tabs layout
│  │  ├─ dashboard.tsx
│  │  ├─ listings/
│  │  │  ├─ index.tsx
│  │  │  ├─ create.tsx
│  │  │  ├─ [jobId].tsx
│  │  │  ├─ [jobId]/edit.tsx
│  │  │  └─ location-picker.tsx
│  │  ├─ applicants/
│  │  │  ├─ [jobId].tsx
│  │  │  └─ [applicationId].tsx
│  │  ├─ messages/
│  │  │  ├─ index.tsx
│  │  │  └─ [threadId].tsx
│  │  ├─ billing/
│  │  │  ├─ index.tsx
│  │  │  ├─ paywall.tsx
│  │  │  └─ success.tsx
│  │  ├─ profile/
│  │  │  ├─ index.tsx
│  │  │  ├─ edit.tsx
│  │  │  └─ verification-status.tsx
│  │  └─ notifications.tsx
│  └─ modal/
│     ├─ image-viewer.tsx
│     ├─ confirm-delete.tsx
│     └─ filter-sheet.tsx
├─ src/
│  ├─ components/
│  │  ├─ common/
│  │  │  ├─ AppHeader.tsx
│  │  │  ├─ Screen.tsx
│  │  │  ├─ EmptyState.tsx
│  │  │  ├─ LoadingState.tsx
│  │  │  ├─ ErrorState.tsx
│  │  │  ├─ Badge.tsx
│  │  │  ├─ Avatar.tsx
│  │  │  ├─ PrimaryButton.tsx
│  │  │  ├─ SecondaryButton.tsx
│  │  │  ├─ IconButton.tsx
│  │  │  ├─ TextField.tsx
│  │  │  ├─ SelectField.tsx
│  │  │  ├─ SearchBar.tsx
│  │  │  ├─ BottomSheet.tsx
│  │  │  └─ SectionHeader.tsx
│  │  ├─ auth/
│  │  │  ├─ RoleSelector.tsx
│  │  │  ├─ SouthAfricanIdField.tsx
│  │  │  ├─ IdUploadCard.tsx
│  │  │  ├─ ProfilePhotoUploader.tsx
│  │  │  └─ VerificationStatusBanner.tsx
│  │  ├─ jobs/
│  │  │  ├─ JobCard.tsx
│  │  │  ├─ JobDetailHeader.tsx
│  │  │  ├─ JobRequirementsList.tsx
│  │  │  ├─ JobFiltersBar.tsx
│  │  │  ├─ PayRateChip.tsx
│  │  │  ├─ DistanceBadge.tsx
│  │  │  ├─ EmployerSummaryCard.tsx
│  │  │  ├─ JobMapMarker.tsx
│  │  │  └─ ListingForm.tsx
│  │  ├─ messaging/
│  │  │  ├─ ChatBubble.tsx
│  │  │  ├─ ChatInput.tsx
│  │  │  ├─ ConversationListItem.tsx
│  │  │  ├─ TypingIndicator.tsx
│  │  │  └─ AttachmentPreview.tsx
│  │  ├─ profile/
│  │  │  ├─ WorkerProfileCard.tsx
│  │  │  ├─ EmployerProfileCard.tsx
│  │  │  ├─ SkillsSelector.tsx
│  │  │  ├─ AvailabilityEditor.tsx
│  │  │  └─ VerifiedBadge.tsx
│  │  └─ billing/
│  │     ├─ SubscriptionStatusCard.tsx
│  │     ├─ PaywallCard.tsx
│  │     └─ PaymentMethodInfo.tsx
│  ├─ hooks/
│  │  ├─ useAuth.ts
│  │  ├─ useCurrentUser.ts
│  │  ├─ useRoleGate.ts
│  │  ├─ useJobListings.ts
│  │  ├─ useNearbyJobs.ts
│  │  ├─ useMessaging.ts
│  │  ├─ useSubscription.ts
│  │  ├─ usePushNotifications.ts
│  │  ├─ useImageUpload.ts
│  │  └─ useLocationPermission.ts
│  ├─ services/
│  │  ├─ supabase/
│  │  │  ├─ client.ts
│  │  │  ├─ auth.ts
│  │  │  ├─ storage.ts
│  │  │  ├─ realtime.ts
│  │  │  └─ rpc.ts
│  │  ├─ api/
│  │  │  ├─ jobs.ts
│  │  │  ├─ profiles.ts
│  │  │  ├─ messages.ts
│  │  │  ├─ subscriptions.ts
│  │  │  ├─ verifications.ts
│  │  │  └─ notifications.ts
│  │  ├─ payments/
│  │  │  ├─ yoco.ts
│  │  │  ├─ webhook-contracts.ts
│  │  │  └─ billing.ts
│  │  ├─ maps/
│  │  │  ├─ geocoding.ts
│  │  │  ├─ distance.ts
│  │  │  └─ places.ts
│  │  └─ validation/
│  │     ├─ auth.ts
│  │     ├─ idNumber.ts
│  │     ├─ listings.ts
│  │     └─ profiles.ts
│  ├─ store/
│  │  ├─ authStore.ts
│  │  ├─ listingsStore.ts
│  │  ├─ messagingStore.ts
│  │  └─ uiStore.ts
│  ├─ lib/
│  │  ├─ formatters.ts
│  │  ├─ dates.ts
│  │  ├─ currency.ts
│  │  ├─ permissions.ts
│  │  ├─ constants.ts
│  │  └─ logger.ts
│  ├─ types/
│  │  ├─ auth.ts
│  │  ├─ user.ts
│  │  ├─ job.ts
│  │  ├─ message.ts
│  │  ├─ billing.ts
│  │  ├─ verification.ts
│  │  └─ navigation.ts
│  ├─ constants/
│  │  ├─ theme.ts
│  │  ├─ routes.ts
│  │  ├─ roles.ts
│  │  ├─ jobTypes.ts
│  │  └─ subscription.ts
│  └─ providers/
│     ├─ AuthProvider.tsx
│     ├─ SessionProvider.tsx
│     ├─ ThemeProvider.tsx
│     └─ NotificationProvider.tsx
├─ supabase/
│  ├─ migrations/
│  ├─ functions/
│  │  ├─ create-checkout-session/
│  │  ├─ payment-webhook/
│  │  ├─ send-push-notification/
│  │  └─ verify-south-african-id/
│  └─ seed.sql
├─ assets/
│  ├─ images/
│  ├─ icons/
│  └─ fonts/
├─ docs/
│  └─ technical-build-plan.md
├─ app.json
├─ package.json
├─ tsconfig.json
└─ babel.config.js
```

**Structure notes**
- Use **Expo Router** on Expo SDK 54 because file-based routing reduces navigation boilerplate and scales well across separate Worker/Employer flows.
- Keep business logic out of screens; screens orchestrate hooks + components only.
- Put all backend integration behind `services/` so Supabase and payments can be swapped or extended later.
- Use `supabase/functions` for secure server-side actions such as payment verification, subscription activation, ID verification orchestration, and push dispatch.

## 2. Navigation Architecture

### Recommended Navigation Pattern
- **Expo Router + React Navigation under the hood**
- **Root Stack** for app boot, auth, and modal flows
- **Role-based Tab Navigators** after login
- **Nested Stacks** inside each tab for details/edit screens
- **Modal presentation** for filters, image viewer, confirmation dialogs, and location pickers

### Navigation by Flow
1. **Public/Auth Flow**
   - Stack navigator
   - Reason: linear onboarding and verification steps

2. **Worker App Flow**
   - Bottom tabs
   - Tabs: Home, Jobs, Messages, Saved, Profile
   - Nested stack in Jobs and Messages for detail views

3. **Employer App Flow**
   - Bottom tabs
   - Tabs: Dashboard, Listings, Messages, Billing, Profile
   - Nested stack in Listings for create/edit/detail flows

### Full Route Map

#### Root
- `/` → boot/splash/auth redirect
- `/(public)/welcome`
- `/(public)/login`
- `/(public)/forgot-password`
- `/(public)/register/role`
- `/(public)/register/account`
- `/(public)/register/verify-id`
- `/(public)/register/upload-id`
- `/(public)/register/profile-photo`
- `/(public)/register/worker-details`
- `/(public)/register/employer-details`
- `/(public)/register/subscription-info`
- `/(public)/legal/privacy-policy`
- `/(public)/legal/terms`

#### Worker Routes
- `/(worker)/home`
- `/(worker)/jobs`
- `/(worker)/jobs/map`
- `/(worker)/jobs/[jobId]`
- `/(worker)/jobs/filters`
- `/(worker)/messages`
- `/(worker)/messages/[threadId]`
- `/(worker)/saved-jobs`
- `/(worker)/notifications`
- `/(worker)/profile`
- `/(worker)/profile/edit`
- `/(worker)/profile/verification-status`

#### Employer Routes
- `/(employer)/dashboard`
- `/(employer)/listings`
- `/(employer)/listings/create`
- `/(employer)/listings/[jobId]`
- `/(employer)/listings/[jobId]/edit`
- `/(employer)/listings/location-picker`
- `/(employer)/applicants/[jobId]`
- `/(employer)/applicants/[applicationId]`
- `/(employer)/messages`
- `/(employer)/messages/[threadId]`
- `/(employer)/billing`
- `/(employer)/billing/paywall`
- `/(employer)/billing/success`
- `/(employer)/notifications`
- `/(employer)/profile`
- `/(employer)/profile/edit`
- `/(employer)/profile/verification-status`

#### Shared Modals
- `/modal/image-viewer`
- `/modal/confirm-delete`
- `/modal/filter-sheet`

### Route Guards
- Unauthenticated users: only public routes
- Authenticated worker: only worker routes
- Authenticated employer: only employer routes
- Employer with inactive subscription: can access billing but cannot access final job posting submission action
- Users pending ID review: limited feature banner, optional restrictions on messaging/posting depending on policy

## 3. Database Schema

**Recommendation:** Use **Supabase Postgres** with Row Level Security.

### Core Tables

#### `users`
Primary identity record linked to auth provider.
- `id` UUID PK (matches Supabase Auth user id)
- `role` enum (`worker`, `employer`)
- `email` text unique
- `phone` text nullable
- `sa_id_number_encrypted` text
- `id_verification_status` enum (`pending`, `under_review`, `verified`, `rejected`)
- `profile_photo_url` text
- `full_name` text
- `is_active` boolean default true
- `last_seen_at` timestamptz
- `created_at` timestamptz
- `updated_at` timestamptz

#### `worker_profiles`
- `user_id` UUID PK/FK → users.id
- `bio` text
- `skills` text[]
- `years_experience` int
- `availability` jsonb
- `preferred_job_types` text[]
- `location_label` text
- `latitude` numeric
- `longitude` numeric
- `max_travel_distance_km` int
- `is_profile_complete` boolean
- `created_at`
- `updated_at`

#### `employer_profiles`
- `user_id` UUID PK/FK → users.id
- `employer_type` enum (`home_owner`, `business_owner`, `property_manager`)
- `business_name` text nullable
- `about` text
- `location_label` text
- `latitude` numeric
- `longitude` numeric
- `is_profile_complete` boolean
- `verified_badge_visible` boolean default false
- `created_at`
- `updated_at`

#### `job_listings`
- `id` UUID PK
- `employer_id` UUID FK → users.id
- `title` text
- `job_type` enum (`cleaning`, `nanny`, `gardening`, `caregiving`, `cooking`, `general_help`, `other`)
- `description` text
- `location_label` text
- `latitude` numeric
- `longitude` numeric
- `hours_per_week` int
- `schedule_notes` text
- `pay_rate_type` enum (`hourly`, `daily`, `weekly`, `monthly`)
- `pay_rate_amount` numeric(10,2)
- `currency` text default `ZAR`
- `requirements` text[]
- `status` enum (`draft`, `published`, `closed`, `archived`)
- `subscription_snapshot_id` UUID nullable
- `expires_at` timestamptz nullable
- `created_at`
- `updated_at`

#### `job_applications`
Needed even though not explicitly requested, because messaging and hiring workflows depend on it.
- `id` UUID PK
- `job_listing_id` UUID FK → job_listings.id
- `worker_id` UUID FK → users.id
- `cover_note` text
- `status` enum (`submitted`, `shortlisted`, `rejected`, `hired`, `withdrawn`)
- `created_at`
- `updated_at`
- unique (`job_listing_id`, `worker_id`)

#### `message_threads`
- `id` UUID PK
- `job_listing_id` UUID nullable
- `worker_id` UUID FK → users.id
- `employer_id` UUID FK → users.id
- `last_message_at` timestamptz
- `created_at`

#### `messages`
- `id` UUID PK
- `thread_id` UUID FK → message_threads.id
- `sender_id` UUID FK → users.id
- `message_type` enum (`text`, `image`, `system`)
- `body` text
- `attachment_url` text nullable
- `read_at` timestamptz nullable
- `created_at` timestamptz

#### `subscriptions`
- `id` UUID PK
- `employer_id` UUID FK → users.id
- `provider` enum (`yoco`, `payfast`, `peach_payments`)
- `provider_customer_id` text nullable
- `provider_subscription_id` text nullable
- `amount` numeric(10,2)
- `currency` text default `ZAR`
- `billing_period` enum (`annual`)
- `status` enum (`pending`, `active`, `expired`, `cancelled`, `failed`)
- `starts_at` timestamptz
- `ends_at` timestamptz
- `last_payment_at` timestamptz nullable
- `created_at`
- `updated_at`

#### `subscription_payments`
- `id` UUID PK
- `subscription_id` UUID FK → subscriptions.id
- `provider_payment_id` text
- `amount` numeric(10,2)
- `currency` text default `ZAR`
- `status` enum (`initiated`, `paid`, `failed`, `refunded`)
- `paid_at` timestamptz nullable
- `raw_payload` jsonb
- `created_at`

#### `id_verifications`
- `id` UUID PK
- `user_id` UUID FK → users.id
- `id_document_front_url` text
- `selfie_photo_url` text
- `sa_id_number_hash` text
- `verification_provider` text nullable
- `review_status` enum (`pending`, `under_review`, `verified`, `rejected`)
- `review_notes` text nullable
- `reviewed_by` UUID nullable
- `reviewed_at` timestamptz nullable
- `created_at`
- `updated_at`

#### `saved_jobs`
- `user_id` UUID FK → users.id
- `job_listing_id` UUID FK → job_listings.id
- `created_at`
- PK (`user_id`, `job_listing_id`)

#### `push_tokens`
- `id` UUID PK
- `user_id` UUID FK → users.id
- `expo_push_token` text unique
- `device_platform` text
- `last_registered_at` timestamptz

### Supporting Database Features
- **Row Level Security policies** on every table
- **PostGIS optional** if advanced geo queries are needed; otherwise store lat/lng and calculate radius using SQL formulas/RPC
- **Database triggers** for `updated_at`
- **RPC functions** for:
  - `get_nearby_jobs(lat, lng, radius_km)`
  - `can_employer_post_job(employer_id)`
  - `create_message_thread_if_missing(worker_id, employer_id, job_id)`
- **Indexes** on:
  - `job_listings(status, job_type)`
  - `job_listings(latitude, longitude)`
  - `messages(thread_id, created_at)`
  - `subscriptions(employer_id, status, ends_at)`
  - `id_verifications(user_id, review_status)`

## 4. Third-Party Service Recommendations

### Recommended Stack Summary
- **Auth:** Supabase Auth
- **Backend/Database:** Supabase
- **Payments:** Yoco
- **Storage:** Supabase Storage
- **Maps/Location:** Google Maps Platform + Expo Location
- **Push Notifications:** Expo Push Notifications

### Auth Provider: Supabase Auth
**Recommendation:** Choose **Supabase Auth** over Firebase Auth.

**Why it fits best**
- Native alignment with **Supabase Postgres**, RLS, storage, and realtime in one platform
- Simpler full-stack architecture for a marketplace MVP and scale-up path
- Easier to model role-based flows with SQL-backed profiles and permissions
- Better fit when subscription gating, verification state, and listing access rules live close to relational data
- Expo SDK 54 works well with Supabase session persistence using secure storage

**Implementation notes**
- Email/password initially, with phone auth as optional later enhancement
- Persist session using `expo-secure-store`
- Add server-side checks so auth alone does not grant posting privileges

### Backend / Database: Supabase
**Why Supabase beats Firebase here**
- Relational schema is a better fit for users, profiles, listings, threads, subscriptions, and verifications
- SQL makes annual subscription gating and audit/reporting easier
- Realtime supports chat and live updates
- Storage and Edge Functions reduce backend surface area
- RLS is strong for privacy and role-based access

### Payment Gateway: Yoco
**Recommendation:** **Yoco** for the first implementation.

**Why Yoco**
- Strong South African market fit and local business familiarity
- Good support for ZAR payments and card checkout flows
- Suitable for a simple annual employer subscription model
- Cleaner first-payment web checkout experience for a mobile MVP than building a more complex billing stack

**Architecture approach**
- App calls a **Supabase Edge Function** to create a checkout session/link
- User completes payment in secure hosted checkout/webview/browser
- Yoco webhook calls secure Edge Function
- Webhook updates `subscriptions` and `subscription_payments`
- App refreshes subscription state before allowing publish/post actions

**Alternatives**
- **PayFast**: viable local alternative with broad familiarity
- **Peach Payments**: strong option if more enterprise flexibility is needed later

### Storage: Supabase Storage
- Separate private buckets:
  - `id-documents` (strict private access)
  - `profile-photos` (public or signed URL strategy)
  - `message-attachments` (private/signed)
- Signed URLs for sensitive content
- Edge Functions broker uploads for sensitive workflows if stricter control is required

### Maps / Location: Google Maps Platform + Expo Location
- Use `expo-location` for device permission and coordinate retrieval
- Use Google Places API for searchable addresses and location autocomplete
- Use `react-native-maps` in Expo-compatible setup for map rendering
- Use geocoding to convert employer-entered addresses into coordinates for job listings

### Push Notifications: Expo Push Notifications
- Best fit for Expo SDK 54 managed workflow
- Register push token per device in `push_tokens`
- Trigger notifications from Supabase Edge Functions when new messages arrive or application status changes

## 5. Component Breakdown

### Common UI Components
- `AppHeader` — standard top bar with title/actions
- `Screen` — safe area + padding wrapper
- `PrimaryButton` / `SecondaryButton` — consistent CTA buttons
- `TextField` / `SelectField` — form inputs
- `Badge` — status labels like Verified, Active, Pending
- `EmptyState` — no data states
- `LoadingState` — skeleton/spinner state
- `ErrorState` — retryable error display
- `BottomSheet` — reusable modal sheet

### Authentication / Verification Components
- `RoleSelector` — choose Worker vs Employer
- `SouthAfricanIdField` — validates SA ID format and checksum/client rules
- `IdUploadCard` — document upload UI
- `ProfilePhotoUploader` — selfie/profile photo capture or upload
- `VerificationStatusBanner` — explains verification progress

### Job Listing Components
- `JobCard` — listing preview in feeds
- `JobDetailHeader` — title, pay, employer, location summary
- `JobRequirementsList` — requirements bullets/tags
- `JobFiltersBar` — job type, pay, distance filters
- `PayRateChip` — highlights rate format
- `DistanceBadge` — worker distance from job
- `EmployerSummaryCard` — quick employer trust/profile summary
- `JobMapMarker` — custom map marker for listings
- `ListingForm` — reusable create/edit listing form

### Messaging Components
- `ConversationListItem` — thread preview
- `ChatBubble` — inbound/outbound message bubble
- `ChatInput` — text input + send + attachments
- `TypingIndicator` — realtime typing state if implemented later
- `AttachmentPreview` — uploaded image/file preview

### Profile Components
- `WorkerProfileCard` — display worker details
- `EmployerProfileCard` — display employer details
- `SkillsSelector` — selectable worker skills list
- `AvailabilityEditor` — schedule and working days editor
- `VerifiedBadge` — trust badge shown after verification

### Billing Components
- `SubscriptionStatusCard` — active/expired/pending state
- `PaywallCard` — explains R50/year access requirement
- `PaymentMethodInfo` — payment explanation and support info

## 6. Key Screens List

### Public / Auth
- **WelcomeScreen** — app introduction and role entry point
- **LoginScreen** — sign in existing users
- **ForgotPasswordScreen** — password recovery flow
- **RegisterRoleScreen** — select Worker or Employer path
- **RegisterAccountScreen** — create account credentials and basic info
- **VerifyIdScreen** — capture and validate South African ID number
- **UploadIdScreen** — upload ID document image
- **ProfilePhotoScreen** — upload/capture user profile photo
- **WorkerDetailsScreen** — complete worker-specific onboarding fields
- **EmployerDetailsScreen** — complete employer-specific onboarding fields
- **SubscriptionInfoScreen** — explains employer subscription before app entry
- **PrivacyPolicyScreen** — legal POPIA/privacy disclosure
- **TermsScreen** — app usage terms

### Worker Screens
- **WorkerHomeScreen** — personalized dashboard with recommended jobs
- **JobListScreen** — browse all available job listings
- **JobMapScreen** — explore jobs visually on a map
- **JobDetailsScreen** — full listing details and employer summary
- **JobFiltersScreen** — adjust search and distance filters
- **SavedJobsScreen** — bookmarked opportunities
- **WorkerMessagesScreen** — conversation list
- **WorkerChatScreen** — direct conversation with employer
- **WorkerProfileScreen** — worker public/private profile overview
- **EditWorkerProfileScreen** — update skills, experience, location, availability
- **WorkerVerificationStatusScreen** — see ID review progress and outcomes
- **WorkerNotificationsScreen** — in-app alerts and updates

### Employer Screens
- **EmployerDashboardScreen** — summary of active listings, applicants, and billing state
- **EmployerListingsScreen** — manage all listings
- **CreateListingScreen** — draft and publish a new job listing
- **ListingDetailsScreen** — inspect one listing and engagement metrics
- **EditListingScreen** — update existing listing details
- **LocationPickerScreen** — choose and confirm listing location on map
- **ApplicantsScreen** — list all applicants for a job
- **ApplicationDetailScreen** — inspect one worker applicant profile
- **EmployerMessagesScreen** — conversation list
- **EmployerChatScreen** — direct conversation with worker
- **BillingScreen** — subscription overview and renewal state
- **PaywallScreen** — subscription purchase entry point
- **BillingSuccessScreen** — post-payment confirmation and next steps
- **EmployerProfileScreen** — employer public/private profile overview
- **EditEmployerProfileScreen** — update employer details
- **EmployerVerificationStatusScreen** — see verification state and guidance
- **EmployerNotificationsScreen** — alerts and updates

### Shared Modal Screens
- **ImageViewerModal** — enlarge uploaded/profile/listing images
- **ConfirmDeleteModal** — confirm destructive actions
- **FilterSheetModal** — quick filters without full page navigation

## 7. Security Considerations

### ID Document Handling
- Store ID documents in a **private storage bucket** only
- Never expose raw storage paths publicly
- Use signed URLs with short expiry for admin/reviewer access
- Encrypt South African ID numbers at rest or store only hashed/partially masked forms where full value is not operationally required
- Minimize retention: keep only what is necessary for compliance and trust workflows
- Log verification access events for admin auditing

### Image Storage Permissions
- Request camera/media library permissions only when needed
- Explain clearly why ID and profile images are required
- Compress images before upload, but preserve legibility for ID documents
- Strip unnecessary metadata where possible before storage

### Payment Security
- Do **not** store raw card data in the app or database
- Use hosted checkout/payment pages from Yoco
- Verify webhook signatures server-side
- Treat webhook update as source of truth for subscription activation
- Keep billing logic in Edge Functions, not in client code

### Privacy / POPIA Considerations
- Provide explicit consent language for collecting ID numbers, ID photos, profile photos, and location data
- Collect only data necessary to provide employment marketplace and trust features
- Publish clear privacy policy and retention policy
- Allow users to request profile/account deletion and define what must be retained for legal/fraud reasons
- Protect direct messages and user contact details from unauthorized access using RLS
- Separate sensitive verification data from normal profile access patterns
- Restrict who can see exact addresses; show approximate locations until trust/action threshold if desired for safety

### Access Control
- Use Supabase **Row Level Security** on every user-owned table
- Workers should only edit their own worker profile and applications
- Employers should only edit their own employer profile and job listings
- Only thread participants can read/send messages in that thread
- Only verified/active employers with valid subscriptions can publish listings

### Operational Security
- Store secrets only in Expo config/environment and Supabase secret storage
- Add rate limiting on auth, messaging, and listing creation via backend controls
- Use audit logs for verification reviews, subscription changes, and admin actions

## 8. Build Phases

### Phase 0: Foundation & Architecture
**Goal:** establish project skeleton and backend baseline.
- Initialize Expo SDK 54 app structure
- Configure Expo Router, TypeScript, linting, env handling
- Set up Supabase project, auth, storage buckets, migrations
- Define theme, route constants, shared types, base components
- Add secure session persistence and provider wiring

**Deliverables**
- Working app shell
- Auth/bootstrap navigation
- Database migrations baseline

### Phase 1: Authentication & Onboarding
**Goal:** users can register and sign in with role-specific onboarding.
- Build welcome/login/register flows
- Add South African ID input validation
- Add ID document upload and profile photo upload
- Build worker and employer onboarding forms
- Create profile records in Supabase
- Show verification pending state

**Deliverables**
- End-to-end account creation
- Role-based route gating
- Verification records stored securely

### Phase 2: Profiles & Verification Operations
**Goal:** complete profile management and trust indicators.
- Build profile view/edit screens
- Add verification status UI and badges
- Implement admin/reviewer support path via Supabase dashboard or internal tools later
- Add privacy/legal screens and consent capture

**Deliverables**
- Complete public/private profile flows
- Trust/verification display rules

### Phase 3: Subscription Billing
**Goal:** employers can pay and unlock posting capability.
- Integrate Yoco checkout flow
- Build paywall and billing status screens
- Implement webhook handling in Edge Functions
- Add subscription gating RPC and client guards

**Deliverables**
- Active subscription lifecycle
- Post-a-job access only for paid employers

### Phase 4: Job Listings Core
**Goal:** employers manage listings, workers browse them.
- Build create/edit/delete/publish listing flows
- Build worker listing feed and detail screens
- Add filters for job type, pay, and distance
- Implement saved jobs and employer profile summary on listings

**Deliverables**
- Marketplace core functional for posting and discovery

### Phase 5: Maps & Location Discovery
**Goal:** location-aware discovery and posting.
- Integrate Expo Location permissions and coordinate capture
- Add Google Places autocomplete and geocoding
- Build map-based jobs screen and location picker
- Implement nearby jobs query and distance sorting/filtering

**Deliverables**
- Nearby jobs map and distance-based discovery
- Accurate listing location capture

### Phase 6: Messaging & Notifications
**Goal:** real-time communication between employers and workers.
- Create threads after apply/contact action
- Build conversation list and chat screens
- Add Supabase Realtime subscriptions
- Register Expo push tokens and send new message notifications

**Deliverables**
- Real-time in-app messaging
- Push alerts for new messages

### Phase 7: Applications, Polish & Release Readiness
**Goal:** complete hiring flow and prepare production release.
- Add applications flow and applicant management
- Improve empty states, error states, loading states
- Add analytics, crash reporting, QA scripts, and performance checks
- Conduct POPIA/legal review and app store readiness checks

**Deliverables**
- Production-ready beta
- Release checklist and monitoring setup

## Recommended Architectural Decisions Summary
- Use **Supabase** as the primary backend because this app is relational and policy-heavy.
- Use **Expo Router** for scalable role-based navigation in Expo SDK 54.
- Use **Yoco** for the first South Africa-focused payment rollout.
- Use **Supabase Storage + private buckets** for ID documents and profile media.
- Use **Expo Push Notifications** and **Supabase Realtime** for messaging.
- Keep sensitive logic such as subscription activation and verification orchestration off the client and inside **Supabase Edge Functions**.

## PDF Export Note
This document is ready to convert into PDF. If you want, the next step should be to save this as `docs/technical-build-plan.md` in the repository and add a generated PDF version such as `docs/technical-build-plan.pdf` through your preferred export workflow.
