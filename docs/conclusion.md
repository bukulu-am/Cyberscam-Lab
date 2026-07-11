# Conclusion

## Summary

The study concluded that a locally relevant, voice-guided, offline-first simulation is an effective and low-cost complement to existing mass-media awareness campaigns in Uganda. CyberScam Lab's six modules — Scam Simulation, Decision Tracking, Video Viewing, Progress Monitoring, Settings, and Backup — accurately played scam scenarios and correctly recorded user decisions. Users rated the experience as highly usable and relevant to their daily exposure to fraud, with all seven functional test cases passing and a strong average usability score (4.4/5 on ease of use, from a simplified SUS with 15 users).

## Limitations

- **Platform:** Released exclusively as an Android application. iOS and web users cannot yet access the platform, though the modular Flutter architecture was intentionally designed to support future ports.
- **Language:** Supports only English and Luganda. Other widely spoken Ugandan languages (e.g. Runyankole, Ateso) are not yet included, limiting reach beyond the Kampala/Wakiso pilot areas.
- **Scenario coverage:** The scenario library covers a finite set of fraud tactics identified during the research period. Newer or highly localized scam variants that emerge afterward won't be reflected without a manual content update.

## Challenges Encountered

- Recruiting a sufficiently large and varied sample of mobile money users willing to discuss fraud experiences in detail — some respondents were hesitant to recount incidents involving personal financial loss.
- Producing natural-sounding Luganda voice recordings that matched the tone of a genuine scam call without being mistaken for an actual threat during testing — required several rounds of script adjustment and re-recording.
- Limited access to detailed, disaggregated fraud statistics directly from telecom providers, requiring heavier reliance on publicly available UCC, Bank of Uganda, and GSMA reports.
- Balancing offline-first functionality with optional cloud backup required a complex local database and synchronization design to avoid data loss during intermittent connectivity.

## Recommendations

- **Scenario Expansion:** Expand the scenario library to cover additional and emerging mobile money fraud tactics, informed by periodic reviews of UCC and telecom fraud reports.
- **Linguistic Diversity:** Add local languages beyond English and Luganda to widen accessibility across Uganda's linguistic communities.
- **User Onboarding:** Integrate a short first-launch tutorial to address the slightly lower independent-use usability score recorded during testing.
- **Strategic Partnerships:** Pursue partnerships with telecom operators, schools, and community organizations to distribute CyberScam Lab more widely and sustain it beyond the academic project period.
- **Platform and Feature Growth:** Extend the application to iOS and web platforms, and explore integration with real-time scam-number reporting services, subject to appropriate data protection and privacy safeguards.
