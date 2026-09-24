# Telemetry

## 1. What is Frontend Telemetry?

Frontend telemetry means collecting user interaction and application usage data from the browser to understand how users are interacting with the product.

We used **Google Tag Manager (GTM), Google Analytics, and Pendo** for frontend/product telemetry.

Examples of telemetry data:

* User clicks
* Page views
* Form submissions
* Feature usage
* User interactions

### Why do we use Frontend Telemetry?

* Understand user behaviour
* Track feature usage
* Measure user engagement
* Support product and analytics teams
* Understand how users interact with the application

---

# Google Tag Manager (GTM)

## 2. What is Google Tag Manager?

Google Tag Manager (GTM) is a tag management system that allows us to manage tracking scripts and analytics events without repeatedly changing the application code.

With GTM, we can:

* Configure tracking from the GTM dashboard
* Create triggers based on user actions
* Fire tags based on those triggers
* Send event data to analytics tools

### Interview Answer

> "I have implemented frontend telemetry in React using Google Tag Manager to track user interactions through dataLayer events and send them to analytics tools."

---

## 3. How does the GTM flow work?

The basic flow is:

**User Action → React → dataLayer → GTM → Tag → Analytics**

### Step-by-step:

1. User interacts with the UI.

   * Button click
   * Page opens
   * Form submission

2. React pushes an event into the GTM dataLayer.

3. GTM listens for that event.

4. GTM trigger matches the event.

5. GTM fires the configured tag.

6. The event is sent to the analytics platform.

---

## 4. What is the dataLayer?

The **dataLayer** is a global JavaScript array/object structure used as a bridge between the application and Google Tag Manager.

The application pushes event information into the dataLayer, and GTM uses that information to trigger the appropriate tags.

Example:

```js
window.dataLayer = window.dataLayer || [];

window.dataLayer.push({
  event: "button_click",
  button_name: "signup"
});
```

### Interview Answer

> "The dataLayer is a global JavaScript array used by GTM to pass event data from the application to Google Tag Manager. React pushes structured event information into the dataLayer, and GTM uses that information to trigger the required tags."

---

## 5. Why did you use GTM instead of directly calling Google Analytics?

### Interview Answer

> "We used GTM because it provides flexibility and centralizes our tracking configuration. Instead of hardcoding every analytics call inside React components, the application sends structured events through the dataLayer, and the tracking logic can be managed through GTM."

### Without GTM

**New tracking requirement → Code change → Build → Deployment**

### With GTM

**React → dataLayer → GTM → Tag/Trigger → Analytics**

This makes tracking configuration easier to manage and reduces the need for application deployments for many tracking changes.

---

## 6. Explain your GTM implementation in React.

### Interview Answer

> "I worked on frontend telemetry in React using Google Tag Manager. We captured user interactions through dataLayer events. For example, when a user clicked a particular button or submitted a form, React pushed a structured event into the dataLayer. GTM listened for those events and triggered the required analytics tags. This allowed the product and analytics teams to track user behaviour without hardcoding every analytics integration directly into the React components."

---

# Pendo

## 7. What is Pendo?

Pendo is a product analytics and product experience platform.

It helps us understand how users interact with an application and provides features such as:

* Product analytics
* User segmentation
* Feature adoption tracking
* In-app guides
* User onboarding
* Contextual tips

### Major Advantage of Pendo

One major advantage is that after integration, Pendo can automatically capture many user interactions without requiring developers to manually instrument every event.

---

## 8. How is Pendo different from Google Analytics?

### Interview Answer

> "Google Analytics primarily focuses on website traffic and event analytics, whereas Pendo is more focused on understanding product usage inside an application. Pendo also provides product experience capabilities such as in-app guides, onboarding, user segmentation, and feature adoption tracking."

| Google Analytics              | Pendo                      |
| ----------------------------- | -------------------------- |
| Website/application analytics | Product usage analytics    |
| Traffic and events            | Feature adoption           |
| User behaviour analytics      | User segmentation          |
| Analytics and reporting       | In-app guides              |
| Event tracking                | User onboarding            |
| Primarily analytics-focused   | Product experience-focused |

---

## 9. How did you use Pendo in the application?

### Interview Answer

> "After integrating Pendo into the application, we configured in-app guides and onboarding flows through the Pendo dashboard. These guides could be displayed based on user segmentation and behaviour without requiring additional code deployments."

For example:

* New users → Show onboarding guide
* Existing users → Don't show onboarding guide
* All users → Show a new feature announcement
* User visits a specific page → Show a contextual tip related to that feature

---

## 10. How does Pendo targeting work?

Pendo allows us to define targeting rules for each guide.

We can control who sees a guide based on:

* User attributes
* User role
* Account type
* New or existing user
* User behaviour
* Page visits
* Specific user actions

### Interview Answer

> "Pendo allows us to define targeting rules for each guide. We can use user attributes and behaviour, such as user type, role, account type, whether the user is new or existing, page visits, or specific actions. Based on those rules, the appropriate guide is displayed to the relevant users."

---

# Telemetry - Cross Questions

## 11. Does Pendo require developers to code every event?

> "No. One of the advantages of Pendo is that after integration, it can automatically capture many user interactions. Developers don't need to manually instrument every individual interaction."

---

## 12. Can Pendo show different guides to different users?

> "Yes. Pendo supports user segmentation and targeting rules, so different guides can be displayed to different users based on their attributes and behaviour."

---

## 13. Do Pendo guides require an application deployment every time?

> "Not necessarily. Once Pendo is integrated, many guide configurations and targeting rules can be managed through the Pendo dashboard without requiring an application deployment."

---

## 14. What is the difference between GTM and Pendo?

### Interview Answer

> "GTM is primarily a tag management layer that helps us manage tracking and send events to analytics or other tools. Pendo is more focused on product analytics and product experience, including feature adoption, user segmentation, onboarding, and in-app guides."

### Easy way to remember:

**GTM = Tracking / Tag Management**

**Google Analytics = Analytics / Reporting**

**Pendo = Product Usage + Onboarding + In-App Guidance**

---

# 15. Explain your overall Telemetry experience.

### 30-Second Interview Answer

> "I have worked on frontend telemetry in React using Google Tag Manager, Google Analytics, and Pendo. With GTM, we used the dataLayer to send structured user interaction events such as button clicks, page views, and form submissions. GTM then used triggers and tags to send those events to analytics tools.
>
> We also integrated Pendo for product analytics and user engagement. Pendo helped us with feature adoption, user segmentation, onboarding, and in-app guides. After the integration, many interactions could be captured automatically, and guides could be configured from the Pendo dashboard based on user attributes and behaviour without requiring additional code deployments."
