<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><p>valign="top" style="border-right: 1px dotted gray;padding-right:25px;"</p></td>
<td><h2 id="owasp_top_10_card_game___game_description">OWASP Top 10 Card Game - Game Description</h2>
<p>The OWASP Top Ten card game is a fun to play poker deck card game that pits the black hats against the white hats to see who can be the first to hack their opponent’s website.</p>
<h2 id="owasp_top_10_card_game___mission_statement">OWASP Top 10 Card Game - Mission Statement</h2>
<p>Using a standard poker card deck, design a card game that combines the concepts of the <strong>OWASP Top 10</strong> and the <strong>OWASP Top 10 Proactive Controls</strong>, for novice level learners, that can be easily converted for use with customized OWASP branded playing cards.</p>
<h2 id="owasp_top_10_card_game___game_overview">OWASP Top 10 Card Game - Game Overview</h2>
<p>The game is designed to be an easy to learn introduction to the risk concepts of the OWASP Top Ten and the best practices control concepts of the OWASP Top Ten Proactive Controls at a novice level in an environment that reflects a sense realism and excitement.</p>
<ul>
<li>The OWASP Top 10 focuses on identifying the most serious web application security risks for a broad array of organizations. A primary aim of the OWASP Top 10 is to educate developers, designers, architects, managers, and organizations about the consequences of the most common and most important web application security weaknesses.</li>
</ul>
<ul>
<li>The OWASP Top 10 Proactive Controls is similar to the OWASP Top 10 but is focused on defensive techniques and controls as opposed to risks. Each OWASP Top 10 Proactive Control technique maps to one or more items in the OWASP Top 10.</li>
</ul>
<p>The four main components of the game (See GitHub - <a href="https://github.com/OWASP/Top-10-Card-Game/">https://github.com/OWASP/Top-10-Card-Game/</a>) include:</p>
<ul>
<li>Threat Agent (TA) deck</li>
<li>Defense Control (DC) deck</li>
<li>Game Play Grid</li>
<li>Game Rules and Instructions</li>
</ul>
<p>The objective of the game is to take control of (PWN) your opponent’s three business websites while protecting your business websites. It is possible to knockout all three of your opponents TA attack websites.</p>
<p>A primary requirement for the game is that it be designed around the standard set of playing cards so that the general public is familiar with the medium facilitating internationalization. The standard two player configuration includes one TA deck and one DC deck for each gamer. The Threat Agent (TA) deck includes two Joker cards that are used to represent a Phishing attack. This brings the TA’s deck to a total of 54. The Defense Control (DC) deck also includes two joker cards that are used to represent White Hat defensive controls. This also brings the DC deck to a total of 54.</p>
<p>During game design, a blue color deck was used to represent the DC team and a red color deck (of the same manufacture) was used to represent the malicious TA team. Cybersecurity activities and training are frequently designed around the concept of red (attacking) and blue (defending) teams.</p>
<p>The game’s detailed play grid (See GitHub - <a href="https://github.com/OWASP/Top-10-Card-Game/">https://github.com/OWASP/Top-10-Card-Game/</a>) is based in part on the attack path flow diagram provided with OWASP’s Top 10 publication. The play grid is designed to help students visualize how threat agents can potentially use many different paths through your application to do harm to your business or organization. The standard two player (four deck) version of the play grid can be summarized as follows:</p>
<p>OWASP Card Game Grid Summary.jpg|View from 3,000 meters</p>
<p>The detailed version of the play grid contains instructional content and provides visual continuity for players:</p>
<p><img src="Game_Grid_Draft.jpg" title="fig:OWASP Card Game Grid" alt="OWASP Card Game Grid" /> &lt;/gallery&gt;</p>
<h2 id="owasp_top_10_card_game___cards">OWASP Top 10 Card Game - Cards</h2>
<p>During game design, four standard poker size playing card decks were used. Each player has one Threat Agent (TA) deck that represents the player’s attack team and one Defense Control (DC) deck that represents the player’s website defense team. Red TA decks and blue DC decks were used during game design.</p>
<p>Threat Agent (TA) attack deck – 54 cards</p>
<ul>
<li>12 Face Cards: The face cards (4 Suits X 3 = 12) are held in a separate deck. The players select their unique combination that must include one Jack, one Queen, and one King. The remaining 9 cards are set aside.</li>
<li>40 TA Attack Cards: There are 40 cards (4 Suits X 10 = 40) that are included in the primary TA attack deck. The 12 face cards are not included in the 40 card TA attack deck.</li>
<li>2 Joker Cards: There are 2 Joker cards included in the primary TA attack deck.</li>
</ul>
<p>Defense Control (DC) deck – 54 cards</p>
<ul>
<li>12 Face Cards: The face cards (4 Suits X 3 = 12) are held in a separate deck. The players select their unique combination that must include one Jack, one Queen, and one King. The remaining 9 cards are set aside.</li>
<li>40 DC Cards: There are 40 cards (4 Suits X 10 = 40) that are included in the primary DC deck. The 12 face cards are not included in the 40 card DC defense deck.</li>
<li>2 Joker Cards: There are 2 Joker cards included in the primary DC deck.</li>
</ul>
<p>Strength and weaknesses may vary among face cards (Jack, Queen, and King), suits (Clubs, Spades, Diamonds, and Hearts), card colors (black and red) and the site card’s face up/down position. Clubs and Spades are black and Diamonds and Hearts are red. Other colors can be substituted as needs require. The game is designed around the standard international, four suit, and two color (red and black) poker deck.</p>
<p>The Masked / Unmasked status (face down / face up) of the attacking and defending sites will affect the strength and weaknesses of the opposing sites (face cards). Face down TA site cards may have more flexible attack options and may be more difficult to defense and face down DC site cards may limit some TA attacks or trigger additional TA workload counts.</p>
<h2 id="owasp_top_10_card_game___setup">OWASP Top 10 Card Game - Setup</h2>
<p>The game’s play grid should be laid out at the start of each game and each player should have ready:</p>
<ul>
<li>Two draw card stacks (one TA team and one DC team).</li>
<li>Two empty discard card stacks (one TA team and one DC team).</li>
<li>Two 5 card hands (one TA team and one DC team). After shuffling, each player selects the top 5 cards from each of their two 40 card decks.</li>
<li>Three DC site face cards should be positioned face down on the playing grid, one in each of the three Business Site positions. These cards should include one Jack, one Queen, and one King of any suit. Individual player strategy will determine the suit mixture.</li>
<li>Three TA site face cards should be positioned face down, one in each of the TA offline bays. These cards should include one Jack, one Queen, and one King of any suit. Individual player strategy will determine the suit mixture.</li>
<li>Each TA face card should be accompanied by a workload counter (dice) or small piece of paper to keep track of the workload counts.</li>
</ul>
<h2 id="owasp_top_10_card_game___start_of_play">OWASP Top 10 Card Game - Start of Play</h2>
<ol>
<li>The three DC site face cards (business websites) are considered online. The DC business site cards will be turned face up as they fall victim to a successful TA Observation attack.</li>
<li>Each player must move at least one of their TA site face cards (attacking site) from the inactive offline rack to the primary online position. The cost is one workload count added to each TA face card moved to an online position. All three TA site face cards may be moved into an online position at the cost of one workload count each.</li>
<li>A coin toss (rock, paper, scissors, etc.) determines who starts game play with the first attack.</li>
</ol>
<h2 id="owasp_top_10_card_game___attack_phase">OWASP Top 10 Card Game - Attack Phase</h2>
<p>The focus of the game is on the TA’s attack phase. The game objective is to attack and defeat (PWN) your opponent’s three DC business websites. At the start of each TA attack round, each player draws sufficient cards to ensure they have 5 cards in both the TA attack hand and the DC business hand. The TA selects an attack card (A1 through A9). If the DC opponent is unable to defense the attack card, the attack is successful. See the Card Attack / Defense Matrix and the instructions about TA Exploit Activities below.</p>
<p>The TA may withdraw the current primary online attack face card and replace it with another attack face card from the online rack at no cost. Whenever a card is moved from the offline rack to the online rack, one workload counter should be added to the card moved online. There is no cost to reposition an online card or return an online card to the offline position.</p>
<ul>
<li>If the move to online results in more than x workload counts, the TA’s online card is no longer effectively masked (considered deprecated) and it is turned face up. Some attacks may be limited.</li>
<li>If the move to online results in more than x workload counts, the TA’s online card is considered decommissioned and must be returned to the offline rack bay.</li>
<li>Once turned face up, the TA face card remains face up.</li>
</ul>
<p>The TA’s attacking card (A1 through A9 and attached A10) is maintained on the grid position marking the successful exploit. The DC loser has the option to name any one of the Top 10 Proactive Controls chosen by the opponent. If correct, two DC cards may be drawn. If incorrect, one DC card may be drawn. The DC player discards any cards in excess of 5.</p>
<p>When the TA’s attack is defeated:</p>
<ul>
<li>Both the attacking TA card (including any attached A10 card) and the defending DC card are moved to their respective discard piles.</li>
<li>The TA's attacking site card earns one workload count.</li>
<li>The DC victor is permitted to draw up to three bonus DC cards for the TA’s attack failure. The DC player discards any cards in excess of 5.</li>
<li>The defeated TA has the option to name any one of the Top 10 risks chosen by the opponent. If correct, no workload count is applied. If incorrect two workload counts are applied to the TA face card. The TA player may use the “hint” table. At the executive level of play, the "hint" table is not permitted.</li>
</ul>
<p>TA card status:</p>
<ul>
<li>Inactive – Offline rack bay.</li>
<li>Active – Online and masked (face down).</li>
<li>Active – Online and unmasked/deprecated (face up).</li>
<li>Decommissioned – Offline rack bay.</li>
</ul>
<p>There are three attack vector pathways. Each pathway includes three defense-in-depth controls that must be defeated:</p>
<ol>
<li>Technology Infrastructure - The suit colors (red and black) represent different technology infrastructures. Infrastructure attack and defense options, strengths and weaknesses may result from color combinations. TAs learn about company weaknesses by using different paths to exploit business, social and technical weaknesses. Each of these paths represents a risk that may, or may not, be serious. Sometimes these paths are trivial to find and exploit, and sometimes they are extremely difficult.</li>
<li>Web Platform - The card suits (Clubs, Spades, Diamonds, &amp; Hearts) represent different web platforms. Web platform attack and defense options, strengths and weaknesses may result from suit combinations. After gaining an understanding of the technologies that support the DC’s web platform, malware can be crafted to exploit weaknesses and misconfigurations.</li>
<li>Web Application - The face cards (Jack, Queen and King) represent sites with different business purposes and different web application layer configurations. Application layer component attack and defense options, strengths and weaknesses may result from face card combinations. The web application layer includes the user interface and other critical functions that if exploited could permit the TA to control the site.</li>
</ol>
<h2 id="owasp_top_10_card_game___threat_agent_ta_exploit_activities">OWASP Top 10 Card Game - Threat Agent (TA) Exploit Activities</h2>
<p>Exploits are designed around five TA team activities (three attacks and two phases):</p>
<ol>
<li>Observation Attack</li>
<li>Weaponization Phase</li>
<li>Assess Web Platform Technical Weaknesses Attack</li>
<li>Site Application Weakness Evaluation Phase</li>
<li>PWN Attack</li>
</ol>
<p>Observation Attack – This includes the concepts of profiling, research, and crafting a reconnaissance strategy. If the TA's Observation Attack is successful, the TA moves to the Weaponization phase. When an Observation exploit is defeated by an effective DC card, the attack round is over. See instructions above for when an attack is defeated.</p>
<p>Weaponization Phase – Based on the results of the Observation phase, the TA will select the best tools and techniques to achieve a presence in the system and to eventually gain system exploit. At the beginning of the Weaponization phase, the TA has several options:</p>
<ol>
<li>End the round without additional workload cost.</li>
<li>Draw up to 3 additional attack cards. After selecting the best cards for the planned exploit, the TA must discard attack cards so the hand has no more than 5 cards. The cost of the additional card draw is to add one workload count to the TA's attacking face card.</li>
<li>Move online TA face card(s) offline. No cost.</li>
<li>Move offline TA face card(s) online. Cost is one workload count per card.</li>
<li>Reposition the TA’s primary online face card to another online position and substitute it with another online card. No cost.</li>
<li>Change attack vector path and launch an Observation Attack on another DC site. No cost.</li>
<li>Launch an Assess Platform Weakness Attack on this site or change the attack vector path and launch an Assess Platform Weakness Attack on any other DC site that is vulnerable due to a previously successful Observation attack. No cost.</li>
<li>Change attack vector path and launch a PWN Attack on any other DC site that is now vulnerable due to a previously successful Assess Platform Weakness Attack. No cost.</li>
</ol>
<p>Assess Web Platform Technical Weaknesses Attack – The purpose of this attack is to evaluate the information gained from the previous phase, craft an effective attack, and assess the technical weaknesses of the opponents DC site web platform. If the attack is successful, the TA moves to the Site Application Weakness Evaluation phase. If the TA's technical weakness attack is defeated, the round is over. See instructions for when an attack phase is defeated.</p>
<p>Site Application Weakness Evaluation – The purpose of this phase is to evaluate the information gained from the previous phases and craft an attack that will effectively implement the TA’s goals. At the beginning of the Site Application Weakness Evaluation phase, the TA has several options:</p>
<ol>
<li>End the round without additional workload cost.</li>
<li>Draw up to 3 additional attack cards. After selecting the best cards for the planned exploit, the TA must discard attack cards so the hand has no more than 5 cards. The cost of the additional card draw is to add one workload count to the TA's attacking face card.</li>
<li>Move online TA face card(s) offline. No cost.</li>
<li>Move offline TA face card(s) online. Cost is one workload count per card.</li>
<li>Reposition the TA’s primary online face card to another online position and substitute it with another online card. No cost.</li>
<li>Change attack vector path and launch an Observation Attack on another DC site. No cost.</li>
<li>Change attack vector path and launch an Assess Platform Weakness Attack on another DC site that is vulnerable due to a previously successful Observation attack. No cost.</li>
<li>Launch a PWN Attack on this site or change the attack vector path and launch a PWN attack on any other DC site that is now vulnerable due to a previously successful Assess Platform Weakness Attack. No cost.</li>
</ol>
<p>PWN Attack – The potential results and future actions following the TA’s PWN attack depend on the status of the TA's attacking face card:</p>
<ul>
<li>If the TA PWN attack is successful, the TA may move to another vector path and launch an attack on another DC site or end the round without additional workload cost.</li>
<li>If the TA is attacking with a face card that is unmasked/deprecated, some attacks may be limited.</li>
<li>If the TA is attacking with a face card that is not unmasked/deprecated and the PWN attack is successful, the TA may also pivot and PWN any of the opponent’s unmasked/deprecated online TA face cards prior to launching an attack in another path vector or ending the round. At the start of the next round, the PWN’d TA face cards (now considered decommissioned) must be returned to the offline rack bay.</li>
</ul>
<p>If the TA's PWN exploit is defeated, the round is over. See instructions for when an attack phase is defeated.</p>
<h2 id="owasp_top_10_card_game___card_attack_defense_matrix">OWASP Top 10 Card Game - Card Attack / Defense Matrix</h2>
<table>
<thead>
<tr class="header">
<th><p>Attacks</p></th>
<th><p>TA Playing Card</p></th>
<th><p>TA Point of View</p></th>
<th><p>Proactive DC</p></th>
<th><p>DC Playing Card</p></th>
<th><p>DC Concepts</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A1</p></td>
<td></td>
<td><p>Ace</p></td>
<td></td>
<td><p>Injection – TAs send simple text based data as part of a command or query that exploits the syntax rules of the targeted system’s interpreter. Many DC teams continue to use unsafe APIs and are lax in reviewing legacy code for injection flaws, keeping data separate from commands and limiting SQL injection mass disclosures.</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>A1</p></td>
<td></td>
<td><p>Ace</p></td>
<td></td>
<td><p>Injection – TAs send simple text based data as part of a command or query that exploits the syntax rules of the targeted system’s interpreter. Many DC teams continue to use unsafe APIs and are lax in reviewing legacy code for injection flaws, keeping data separate from commands and limiting SQL injection mass disclosures.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>A2</p></td>
<td></td>
<td><p>2</p></td>
<td></td>
<td><p>Broken Authentication – System flaws allow TAs to compromise passwords, keys, or session tokens, or to assume other users’ identities. Privileged accounts are frequently targeted. The prevalence of broken authentication is widespread across the DC landscape due to poor design and weak implementation of identity and access controls. Effective reconnaissance will help identify systems that may be using admin default credentials.</p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>A3</p></td>
<td></td>
<td><p>3</p></td>
<td></td>
<td><p>Sensitive Data Exposure – TAs steal clear text data off the server, while in transit, or from the users browser. Over the last few years, this attack has seen successful TA exploits. DC teams are not ensuring that the business is encrypting sensitive data. Sensitive data maybe stored or cached long after it is needed for any business purpose. When crypto is employed, weak key generation and management, and weak algorithm, protocol and cipher usage is common, particularly for weak password hashing storage techniques. For data in transit, server side weaknesses are mainly easy to detect, but hard for data at rest.</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>A4</p></td>
<td></td>
<td><p>4</p></td>
<td></td>
<td><p>XML External Entities (XXE) - TAs upload hostile content to XML processors or documents. DC management continues to disregard this risk and frequently fails to support funding for Web Application Firewalls, XXE testing and essential developer training to identify and mitigate XXE.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>A5</p></td>
<td></td>
<td><p>5</p></td>
<td></td>
<td><p>Broken Access Control – TAs know that flawed applications and APIs may allow users to move beyond management’s intended permissions. Access control weaknesses are common due to the lack of automated detection and effective functional testing by application developers.</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>A6</p></td>
<td></td>
<td><p>6</p></td>
<td></td>
<td><p>Security Misconfiguration – TAs exploit unpatched flaws or access default accounts, unused pages, unprotected files and directories to gain unauthorized access or knowledge of the system. Without a robust and mature DC process, it is virtually impossible for companies to properly harden all assets resulting in application stack security misconfigurations permitting successful exploits of network services, platforms, web servers, application servers, databases, frameworks, custom code, and pre-installed virtual machines, containers, or storage.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>A7</p></td>
<td></td>
<td><p>7</p></td>
<td></td>
<td><p>Cross-Site Scripting (XSS) – TA input is not prevented from updating a web page with malicious data resulting in hijacked user sessions, defaced web sites, redirected users and malware. DC teams are not following the OWASP XSS Prevention Cheat Sheet and TAs around the globe are leveraging this risk. It is found in approximately two-thirds of all applications.</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>A8</p></td>
<td></td>
<td><p>8</p></td>
<td></td>
<td><p>Insecure Deserialization – TAs exploit weaknesses in applications and APIs that permit the deserialization of hostile TA data. TA exploitation of deserialization is difficult, as off the shelf exploits rarely work without changes or tweaks to the underlying exploit code.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>A9</p></td>
<td></td>
<td><p>9</p></td>
<td></td>
<td><p>Known Vulnerabilities - TAs identify weak components through scanning or manual analysis and customize attack exploits. Prevalence of this issue in the business community is widespread. Component-heavy development patterns has resulted in development teams not understanding which components they use in their application or API, much less keeping them up to date. DC teams may be limited in their efforts to scan, identify and remove unnecessary functions and monitor libraries.</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>Black Hat</p></td>
<td></td>
<td><p>Joker</p></td>
<td></td>
<td><p>Phishing attack – Phishing controls include day-to-day procedures and education and are rarely designed with the holistic view necessary to mount an effective defense. There are few DC precautions that application writers can follow to reduce this risk. DC and business management have historically been lax in addressing phishing controls.</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>A10</p></td>
<td></td>
<td><p>10</p></td>
<td></td>
<td><p>Logging &amp; Monitoring - TAs rely on ineffective application runtime security logging, inconsistent operational data reviews, and the poor overall management of monitoring activities, coupled with weak responses by the DC team, to achieve their goals without being detected. This card represents additional malware that supports the attack card (A1 through A9). It is used during the attack phase. It is not a stand-alone attack card. The A10 card may be added to support the TA’s attack card during the current or subsequent attack rounds. The A10 card can only be played during an Assess Web Platform Technical Weaknesses Attack or PWN Attack. The TA’s A10 card may be any color.</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td><p>White Hat</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>
<table>
<thead>
<tr class="header">
<th><p>Special Attack and Defense Rules</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Observation Attack - If the TA site is not masked, the color of TA’s attacking card (A1 through A9) must match the color (red or black) of the TA’s site card.</p></td>
</tr>
<tr class="even">
<td><p>Assess Web Platform Technical Weaknesses Attack - If the TA site is not masked, the suit of the TA’s attacking card (A1 through A9) must match the suit (hearts, diamonds, spades, or clubs) of the defending DC site card.</p></td>
</tr>
<tr class="odd">
<td><p>PWN Attack - If the TA site is not masked, the attacking TA site (Queen or King) must match the face card (Queen or King) of the defending DC site card. An unmasked Jack may still attack any other face card.</p></td>
</tr>
</tbody>
</table>
<h2 id="owasp_top_10_card_game___ta_hint_table">OWASP Top 10 Card Game - TA Hint Table</h2>
<table>
<thead>
<tr class="header">
<th><p>OWASP Top 10 Risks</p></th>
<th><p>TA Playing Card</p></th>
<th><p>TA Hint</p></th>
<th><p>OWASP Top 10 Risks</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A1</p></td>
<td></td>
<td><p>Ace</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>A2</p></td>
<td></td>
<td><p>2</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>A3</p></td>
<td></td>
<td><p>3</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>A4</p></td>
<td></td>
<td><p>4</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>A5</p></td>
<td></td>
<td><p>5</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>A6</p></td>
<td></td>
<td><p>6</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>A7</p></td>
<td></td>
<td><p>7</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>A8</p></td>
<td></td>
<td><p>8</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>A9</p></td>
<td></td>
<td><p>9</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>A10</p></td>
<td></td>
<td><p>10</p></td>
<td></td>
</tr>
</tbody>
</table>
<h2 id="owasp_top_10_card_game___dc_hint_table">OWASP Top 10 Card Game - DC Hint Table</h2>
<table>
<thead>
<tr class="header">
<th><p>OWASP Top 10 Proactive Controls</p></th>
<th><p>DC Playing Card</p></th>
<th><p>DC Hint</p></th>
<th><p>OWASP Top 10 Proactive Controls</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>C1</p></td>
<td></td>
<td><p>Ace</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>C2</p></td>
<td></td>
<td><p>2</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>C3</p></td>
<td></td>
<td><p>3</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>C4</p></td>
<td></td>
<td><p>4</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>C5</p></td>
<td></td>
<td><p>5</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>C6</p></td>
<td></td>
<td><p>6</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>C7</p></td>
<td></td>
<td><p>7</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>C8</p></td>
<td></td>
<td><p>8</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>C9</p></td>
<td></td>
<td><p>9</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>C10</p></td>
<td></td>
<td><p>10</p></td>
<td></td>
</tr>
</tbody>
</table>
<h2 id="owasp_top_10_card_game___licensing">OWASP Top 10 Card Game - Licensing</h2>
<p>This card game is free to use. It is licensed under the Creative Commons Attribution ShareAlike 3.0 license, so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p>
<p>Special customized card decks are available through OWASP. These are standard poker decks that have been modified to enhance the game’s learning experience. These decks and the related play grid contain OWASP copyrighted images and related descriptions and all rights are reserved. Generally, these decks (and play grid) are updated as the new versions of the OWASP Top 10 are released. All profit derived from the sale of the customized decks (and other related items) are used to further OWASP global efforts. See [add reference / link here] for additional information and examples.</p>
<h2 id="owasp_top_10_card_game___roadmap">OWASP Top 10 Card Game - Roadmap</h2>
<p>Phase 1 of the project is complete and it resulted in the completion of the proof of concept, mission statement, short team goals, long team goals and a basic game prototype.</p>
<p>Phase 2 of the project includes assistance from the OWASP foundation, setting up a project Wiki page, setting up a GitHub page, and adding the project to the OWASP project inventory (Incubator Status).</p>
<p>Phase 3 of the project includes looking for other people to help lead and contribute to the project. Areas of need and the corresponding volunteer are listed in the “Getting Involved” section of this Wiki.</p>
<p>Phase 4 will move the project to the Labs phase.</p>
<p>Phase 5 will move the project to the Flagship phase.</p>
<p>Phase 6 addresses the project’s long team goals. It will incorporate the basic OWASP Top 10 Card Game as presented in the Flagship phase along with special customized card decks that will be available through OWASP. These are standard poker decks that have been modified to enhance the game’s learning experience. These decks and the related play grid contain OWASP copyrighted images and related descriptions and all rights are reserved by OWASP.</p>
<h2 id="owasp_top_10_card_game___getting_involved">OWASP Top 10 Card Game - Getting Involved</h2>
<table>
<thead>
<tr class="header">
<th><p>Task</p></th>
<th><p>Volunteer</p></th>
<th><p>Responsibilities</p></th>
<th><p>Status</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Technical Jargon Watchdog</p></td>
<td></td>
<td><p>Add name and contact information here</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Game Play Grid Layout and Design Coordinator</p></td>
<td></td>
<td><p>Add name and contact information here</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Game Play Instructions Coordinator</p></td>
<td></td>
<td><p>Add name and contact information here</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Trial Game Coordinator</p></td>
<td></td>
<td><p>Add name and contact information here</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Card Layout and Design Coordinator</p></td>
<td></td>
<td><p>Add name and contact information here</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Card Image and Design Coordinator</p></td>
<td></td>
<td><p>Add name and contact information here</p></td>
<td></td>
</tr>
</tbody>
</table>
<h2 id="owasp_top_10_card_game___project_resources">OWASP Top 10 Card Game - Project Resources</h2>
<p>GitHub - <a href="https://github.com/OWASP/Top-10-Card-Game/">https://github.com/OWASP/Top-10-Card-Game/</a></p>
<h2 id="owasp_top_10_card_game___project_leader">OWASP Top 10 Card Game - Project Leader</h2>
<p><a href="mailto://dennis.johnson@owasp.org">Dennis Johnson</a></p>
<h2 id="owasp_top_10_card_game___related_projects">OWASP Top 10 Card Game - Related Projects</h2>
<p>None</p>
<h2 id="owasp_top_10_card_game___lessons_learned">OWASP Top 10 Card Game - Lessons Learned</h2>
<table>
<thead>
<tr class="header">
<th><p>Number</p></th>
<th><p>Title</p></th>
<th><p>Description</p></th>
<th><p>Recommendation</p></th>
<th><p>Owner</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td></td>
<td><p>Technical Complexity</p></td>
<td></td>
<td><p>The OWASP Top 10 and the OWASP Top Ten Proactive Controls are abstractions of complex real life technical challenges and solutions. Because the card game is a abstraction of the Top 10 risks and controls, it is important to be mindful that the game can easily grow in complexity beyond the intended scope of the novice learner</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td></td>
<td><p>Operational Complexity</p></td>
<td></td>
<td><p>Even through the game is based on the common poker card deck and a simple game grid, there is ample opportunity for the game to grow in complexity beyond the intended scope of the novice learner</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td></td>
<td><p>Card Formulations</p></td>
<td></td>
<td><p>During the prototype design process, it was determined that increasing or decreasing the number of attack cards based on the Top 10's risk calculation process, was not meaningful to the games's purpose and only added complexity</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td></td>
<td><p>Heavy Lifting Already Completed by Other Teams</p></td>
<td></td>
<td><p>The game relies on the professionally developed and presented work completed by the Top 10 risk and controls project teams</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td></td>
<td><p>Use of Die</p></td>
<td></td>
<td><p>During the prototype design process, it was determined that the workload count added for each attack failure was probably best tracked by each player using a six sided die</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td></td>
<td><p>Workload Counts</p></td>
<td></td>
<td><p>During the prototype design process, the appropriate number of workload counts that should be accumulated for an attacking threat agent website to be unmasked or decommissioned was not finalized</p></td>
</tr>
<tr class="odd">
<td><p>7</p></td>
<td></td>
<td><p>Gamer Education</p></td>
<td></td>
<td><p>The purpose of the game is to provide an interesting and fun experience and also help the gamer to learn about the OWASP Top 10 risks and controls</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td></td>
<td><p>Game Grid</p></td>
<td></td>
<td><p>The initial prototype was designed with a more simple grid; however, this proved to be a bit boring for the gamer. The current game grid reflects design aspects taken from the OWASP Top 10 publication and a layered attack vector that is segmented into five defense-in-depth activities that are summarized with the mnemonic OWASP</p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td></td>
<td><p>Card Back Designs</p></td>
<td></td>
<td><p>At a minimum, the TA deck should be a color different than the DC deck. A red TA deck and a Blue DC deck seem to augment a more realistic learning experience. Using cards with the same design pattern, made it easy to mix up the player cards</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td></td>
<td><p>Optional Game Formats</p></td>
<td></td>
<td><p>Consider play formats for other than two players</p></td>
</tr>
<tr class="odd">
<td><p>11</p></td>
<td></td>
<td><p>Stalemate</p></td>
<td></td>
<td><p>Similar to chess, it has been recommended that when a stalemate occurs, the game ends as a draw.</p></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")