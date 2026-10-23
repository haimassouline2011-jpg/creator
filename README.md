# Creator

Jeu mobile de construction : chaque joueur a une maison dans une ville partagée, et la construit et l'améliore (murs, terrain, meubles). Style 3D "pixel art" (voxels).

## État actuel : version 1.89 (Android, PC Windows, Mac et iPhone web : apk/creator-1.89.apk, apk/creator-1.89-pc.zip, apk/creator-1.89-mac.zip, dossier web/, en ligne sur https://haimassouline2011-jpg.github.io/creator/)

## Version 1.89 (2026-10-23)
- Hôpitaux de ville : Paris (Hôtel-Dieu, au nord de l'Étoile, paris.HOPITAL) et Tel Aviv (Ichilov, rangée libre au sud de Rothschild, telaviv.HOPITAL), construits par hopitaux.gd comme l'Ospedale de Rome (comptoir des urgences : +60 PV pour 40 px). Après un KO, sante._city_hospital renvoie à l'hôpital de la ville (dans un centre commercial : la ville d'entrée, marches.back_city), sinon Hong Kong. L'Hôtel-Dieu est construit à la fin de paris.ensure_built pour ne pas décaler le tirage des immeubles (labels < 150).
- Lance-flammes (weapons.gd « lance_flammes », type flamme, 88 000 px, réservoir 100, portée 13 m) : jet de feu en cône (20° de chaque côté), 22 dégâts par bouffée × 10/s sur chaque cible du cône, brûlure 8 dégâts / 0,5 s pendant 3 s (combat._flame, burns). Jet CPUParticles3D + lueur + grondement en boucle (W.set_flame), visible chez les autres joueurs (net « fl »). Icône icones/arme_lance_flammes.png (rendu du modèle).
- Radio : démarre sur la station Pop (tags Jamendo pop+dance+upbeat, clé radio.cfg « station3 »). Gili ne crie plus (boss._cry ne joue plus de son).
- Radio (casque) en haut après le sac, 66 × 66, panneau dessous ; bouton Parler retiré (voice_btn caché, sert encore aux appels) ; Émotion en pilule en bas après les raccourcis, choix des émotions au-dessus (layout _v=3 oublie radio/emotion).
- Rangée du haut : Ma ferme et GM après Guide et Cartes (même taille 130 × 53), enveloppe et sac à dos côte à côte en haut (layout messages/sac ; anciennes places oubliées via _v=2 dans user://touches4.json).
- Échange entre joueurs : onglets Objets / Cartes ; on peut échanger ses cartes à collectionner (clé `carte:<collection>_<n°>`, cartes.count/take/receive). Recevoir la dernière carte d'une collection donne son cadeau.
- Jérusalem retirée à la demande d'Alain (jerusalem.gd supprimé, ses textes de lang.gd, voix hébreu de la ville, contrôle « lieu saint » de parcs.gd). Les plats de rue de Jérusalem restent en vente, à Tel Aviv (carte « tlv » de plats.gd). Les billets « Jérusalem » d'une ancienne sauvegarde deviennent des billets « Rome ».
- Rome (rome.gd, même zone z - 12000, porte 2 de l'aéroport, vol CR111, billet 80 px aux guichets ; ville construite seulement au premier passage, comme Paris et Hong Kong) : piazza Venezia à l'arrivée avec le Vittoriano (escalier, colonnade, statue équestre, quadriges), via del Corso, Colisée (64 arcades sur trois étages et attique, côté sud en ruine, gradins, arène et souterrains), arc de Constantin, Forum romain (colonnes, temples), fontaine de Trevi (« Jeter une pièce dans la fontaine », 1 px), Panthéon (rotonde, coupole, portique), place Navone (trois fontaines, obélisque, Sant'Agnese, terrasses), place d'Espagne (escalier de 18 marches praticable, Trinità dei Monti, obélisque), Tibre avec quatre ponts dont le pont Saint-Ange et ses anges, château Saint-Ange, place Saint-Pierre (colonnade, obélisque, fontaines, basilique et coupole), villa Borghèse (pins parasols, lac et son temple, galerie). Rues de palais ocre, orange, rose et jaune avec toits de tuiles, volets verts et balcons, piazzette avec fontaine, pins et café.
- Rome a tout ce qu'ont Paris et Hong Kong : centre commercial « Marché Rome » (10 magasins) et « Marché Mondial » à l'arrivée, magasins des joueurs, armurerie et supermarché en ville (_city_shops), boutiques italiennes en rez-de-chaussée (trattoria, gelateria, pizzeria, caffè, souvenirs, mode avec essayage), 11 plats romains (carte « rome » : supplì, cacio e pepe, amatriciana, pizza al taglio, saltimbocca, carciofi, gnocchi, gelato, tiramisù, maritozzo, espresso), 4 souvenirs (mini Colisée, amphore, buste romain, cafetière moka), 3 hôtels (Palazzo del Corso, Grand Hotel Imperiale, Hotel Trastevere), parcs de repos (villa Borghèse, place Navone), bus 64, métro Linea B et Leonardo Express (Fiumicino), foule et voitures, Polizia di Stato, hôpital (soins 60 PV, 40 px), borne de recharge, lampadaires et fenêtres allumées la nuit, carte de la ville sur la minimap, ligne dans le Guide. Les habitants et les vendeurs parlent italien (voix.gd « it », voix it-IT) ; dans les centres commerciaux d'une ville, ils parlent la langue de la ville. Gardes suisses devant Saint-Pierre, centurions au Colisée.
- Page commerçants : la ville « Jérusalem » devient « Rome » (site_src/commercants.html, supabase/commercants.sql, supabase/tout-en-une-fois.sql). Supabase : supabase/rome.sql à lancer seulement si la table commercants a été créée avant le 23/10 à 8 h 46 (sinon déjà bon ; le relancer ne fait pas de mal).
- À la publication : recopier site_src/commercants.html vers site/ (le site du dépôt a encore Jérusalem). Les numéros des magasins de la porte 2 ont changé (les magasins de Jérusalem de la 1.88 deviennent ceux de Rome).
- Captures `captures/rome-*.png`.

## Version 1.88 (2026-10-23)
- Bouton « Donner des Pixart » (+1/+5/+10/+50/+100) sur le profil d'un joueur, visible seulement pour Alain (code propriétaire ALAIN…). Message réseau `pixart_don`, accepté seulement si l'envoyeur a le drapeau `al` dans son bonjour.
- Pixart : plus aucune source dans le jeu (boss, méga-boss, arbres, classement, événements auto, récompenses, accueil, concours), seulement les événements organisés par Alain ; tous les joueurs repartent à 0 une fois (clé de sauvegarde "pixart_zero").
- Pièces Pixart et pixels du porte-monnaie : une seule pièce qui tourne sur elle-même en boucle (inventory.gd), plus de pile de tranches ni d'éclat en croix.
- La voiture monte sur les petites marches (bord du sable vers la route, trottoirs, rebords jusqu'à 55 cm) au lieu de rester bloquée (main._drive : test_move vers le haut puis en avant).
- Métiers entre joueurs (metiers.gd, tuile « Métiers » et appli « Services » du téléphone) : taxi, livreur, policier, médecin. En service, le métier s'affiche sur la plaque (plaques.set_job) ; les autres joueurs appellent depuis « Appeler un service » et paient quand c'est fait : taxi au mètre à la descente (10 px + 2 px / 10 m, passagers.gd), livraison d'un objet du sac (prix + 20 px), soins (60 PV, 40 px), police (60 px payés par la ville, contrôle d'un joueur recherché : amende 150 px). Appeler Police ou Ambulance au téléphone prévient aussi les joueurs en service. Sans client : petites missions PNJ dans Hong Kong (20 à 80 px). Réseau : mt, mt_dem, mt_ok, mt_non, mt_fin, mt_colis(_non), mt_ctrl(_ok), mt_paye ; champ « mt » dans bonjour. Sauvegarde « metier ».
- Commerces tenus par les joueurs (commerce.gd, tuile « Commerces » et bouton dans « Mon magasin » du marché) : son magasin devient un restaurant (30 plats) ou une boutique de vêtements (11 t-shirts, couleur r_haut). Stock acheté en gros (lots de 10 à 40 %), prix choisis (±1/±10) ; les clients PNJ achètent selon le prix, aussi hors ligne (ventes comptées à la connexion, 12 h au plus) ; les objets du marché pas trop chers partent aussi doucement. Les joueurs en ligne achètent dans l'onglet « En ville ». Réseau : com, com_achat, com_ok, com_non. Sauvegarde « commerce ».
- Événements à heure fixe (evenements.gd, tuile « Événements » et appli du téléphone) : chaque jour, à la même heure pour tous (heure de Paris calculée depuis l'heure UTC, été/hiver compris) : 13 h Chasse au trésor (5 coffres cachés dans les rues de Hong Kong, mêmes cachettes pour tous ce jour-là, indice direction + distance, 2 500 px par coffre, un coffre ouvert disparaît chez tous), 18 h Rallye de Hong Kong (14 portes au chrono, à pied ou en véhicule, repère sur la carte), 21 h Raid du boss géant (le méga-boss de boss.gd apparaît pendant 30 min, les dégâts comptent). Annonces 10 min et 1 min avant (bandeau, message, téléphone), bandeau en bas pendant l'événement, page avec compte à rebours. À la fin : pixels + 1 Pixart pour chaque participant, 20 000 px + 3 Pixart au 1er, 8 000 px + 1 Pixart aux 2e et 3e (s'il y a au moins 2 joueurs). Réseau : ev (score), ev_tr (coffre trouvé). Sauvegarde « evenements ».
- Récompenses (recompenses.gd, tuile « Récompenses » et appli du téléphone) : cadeau du jour sur 7 jours (500 à 8 000 px, le 7e jour +3 Pixart et un objet ; un jour manqué remet la série à 1), proposé à la connexion. Passe de saison mensuel, 30 paliers de 400 XP de saison (XP des niveaux via levels.gain, cadeau du jour, événements) : piste gratuite (px, Pixart tous les 5 paliers, objet commun au 15e, rare au 30e) et piste Premium si Premium actif (double de px, Pixart tous les 3 paliers, objets rares aux 10e/20e/30e, +10 Pixart au 30e). Remise à zéro le 1er du mois (heure de Paris). Sauvegarde « recompenses ».
- Accueil des nouveaux (accueil.gd) : les premières minutes guidées d'un nouveau compte, une carte dorée en haut de l'écran, étape par étape : bouger (15 m, cercle doré autour du joystick), ouvrir la carte, vélo offert puis balade jusqu'à un lieu de la carte (rayon doré + flèche), premier achat (bouton « Commander un plat »), se faire un ami ou parler à Sami le guide, prendre le cadeau du jour. 100 à 300 px par étape, 1 000 px + 1 Pixart à la fin. Bouton « Passer » ; « Revoir l'accueil » dans le Guide reprend l'accueil (ou le rejoue, sans récompenses). Les anciennes parties (sauvegarde sans « accueil », niveau > 1, garage, quêtes ou maison) ne le voient pas. Pendant l'accueil, le Guide et le cadeau du jour ne s'ouvrent plus tout seuls. Sauvegarde « accueil » (etat, i, paye, dest) ; main.pixels_spent compte les pixels dépensés.
- Concours de maisons (concours.gd, tuile « Concours de maisons » et appli « Concours ») : chaque semaine (lundi à dimanche, heure de Paris) on inscrit sa maison (20 blocs au moins ; la maison est envoyée avec l'inscription, visible même si son propriétaire n'est pas en ligne), on visite celles des autres (« Visiter » -> voisins.go) et on les note de 1 à 5 ★, une fois par maison et par semaine, jamais la sienne (barre de vote en bas pendant la visite). Le lundi, la meilleure moyenne de la semaine passée (au moins 2 votes) est annoncée à tous ; le gagnant reçoit 25 000 px + 5 Pixart et « PLUS BELLE MAISON » en doré sur sa plaque toute la semaine (plaques.set_crown, champ « cm » dans bonjour). Onglet « Gagnants » (10 dernières semaines). Votes en direct : réseau « cc » (ins, vote ; le propriétaire voit « X a donné N ★ à ta maison »). Supabase : supabase/concours.sql à exécuter (sans les tables : « Le concours n'est pas encore activé sur le serveur »). Sauvegarde « concours ».
- Circuit & Stade (circuit.gd, stade.gd ; tuile « Circuit & Stade » et appli du téléphone, zone x - 12000, z + 12000, sur la carte) : vrai circuit fermé de 2,3 km (asphalte, vibreurs rouge et blanc dans les virages, glissières, arche « Départ · Arrivée » et damier, tribune, stands, kiosque de location). Contre-la-montre : chrono lancé sous l'arche, temps des secteurs S1/S2/S3 avec écart au record, meilleur tour gardé (+100 px par record), fantôme du record (fichier local user://circuit_ghost.json). Véhicule : le sien (voitures et motos du garage, gratuit) ou une location (Furia 300 px, Orage 250, Éclair 200, Nero 150), rendue en quittant le complexe. Course à plusieurs (2 joueurs ou plus au circuit) : compte à rebours, grille sous l'arche, 2 tours, 1 500 px au vainqueur et 200 px à chaque arrivée (réseau « cr » : go, in, fin). Classement en ligne des meilleurs tours : supabase/circuit.sql à exécuter (sans la table : « pas encore activé », le record reste sur l'appareil). Sauvegarde « circuit ».
- Stade (stade.gd) : terrain de foot (buts, filets, tribune, pylônes) et terrain de basket (paniers, raquettes, ligne à 3 points) avec un ballon physique. « Frapper » près du ballon (direction de la caméra) ou on le pousse en marchant ; au basket on ramasse le ballon et « Lancer au panier » (plus loin = plus dur, 3 points au-delà de 6,75 m). Matchs de 5 minutes, Bleus contre Rouges, tableau des scores ; seul, des joueurs du jeu complètent les équipes (gardiens au foot) ; à plusieurs, équipes automatiques et le dernier qui touche le ballon envoie sa position 10 fois par seconde (réseau « bl », « sp_match », « sp_but »). But +100 px, victoire +500 px, XP « sport ».
- Jérusalem (jerusalem.gd, zone z - 12000, porte 2 de l'aéroport, vol CR111 ouvert, billet 80 px aux guichets) : vieille ville dans ses remparts de pierre dorée avec créneaux, porte de Jaffa et porte de Damas, Tour de David (citadelle et minaret), souk couvert de la rue David et ruelle de la porte de Damas (échoppes d'épices, céramique, tissus, lanternes, douceurs), esplanade du Mur occidental, dôme doré vu de loin sur une haute esplanade sans accès (silhouette seulement). Ville nouvelle : rue Jaffa et son tramway (deux rames, 3 arrêts : « Tramway vers… » téléporte à l'arrêt suivant), marché Mahané Yehuda couvert, rue Mamilla, Knesset et sanctuaire du Livre, immeubles en pierre de Jérusalem, oliviers et cyprès. Panneaux en hébreu + français/anglais, habitants qui parlent hébreu (voix.gd), policiers aux portes, carte de la ville sur la minimap.
- Jérusalem, lieu saint : dans la vieille ville, ni combat ni attaque (parcs.safe -> jerusalem.holy), pas d'armurerie ; les magasins des joueurs, l'armurerie et le supermarché sont dans la ville nouvelle (_city_shops, après les centres commerciaux pour garder les numéros des magasins).
- Achats à Jérusalem : 4 meubles du souk (epices 60 px, ceramique 120, tapis 180, lanterne 90 qui éclaire) ; 9 plats de Jérusalem (carte « jr » de plats.gd : shawarma, sabich, ka'ak, meorav yerushalmi, bourekas, rugelach, kugel, jus de grenade, houmous et fèves) au souk, à Mahané Yehuda et au Café Mamilla ; à Mamilla aussi mode (essayage), lustre et statue.
- Page commerçants (idée 10) : sur le site, `commercants.html` (lien « Commerçants » dans espace.html), un vrai commerçant connecté crée sa boutique : nom, catégorie, description FR (EN/HE facultatifs), site https, logo et jusqu'à 8 produits (photo, nom, prix en €, lien). Photos réduites dans le navigateur puis rangées dans le seau Storage public `commerces/<son id>/`. Elle reste « en attente » ; toute modification la remet en attente. Section Administration visible seulement des comptes de la table `commerce_admins` (valider / remettre en attente / supprimer). SQL : `supabase/commercants.sql` (à lancer, puis la ligne `insert into commerce_admins` avec son e-mail).
- Jeu : `commercants.gd` lit les boutiques validées (REST, clé publique, marche sans compte), les place dans l'ordre des id dans un magasin libre de leur ville (Hong Kong, Paris, Tel Aviv, Jérusalem ; à défaut celui d'un voisin du jeu), logo à côté de l'enseigne, produits encadrés sur les murs avec nom et prix. Devant la porte : « Visiter le site » ou « Visiter la boutique virtuelle » (fiche avec description et produits qui ouvrent leur lien). Liste et images (256 px logo, 320 px photos) gardées dans user:// pour le hors-ligne. Tables absentes : « Boutiques des commerçants : pas encore activées » dans la liste du Marché. La sauvegarde garde l'ancien état du magasin (rien ne reste si la boutique disparaît). Captures `captures/commercants-*.png`.

## Version 1.87 (2026-10-22)
- Éclairage intérieur beaucoup plus fort, en blanc chaud, même la nuit (interieur.gd : lumière ambiante relevée dedans ; nuit.gd : plafonniers plus puissants, sans doublon dans le bâtiment où l'on est).
- Correction : le jeu web plantait au démarrage (iPad : « Division by zero ») car un son était joué avant la création des lecteurs (sounds.play : % shots.size() avec 0).
- Web (iPad « WebGL context lost ») : pas de petits morceaux (main.chunk_of), 4 plafonniers au lieu de 10 (nuit.gd), limites de lumières par défaut (project.godot .web).
- Web iPad/iPhone (mémoire graphique) : visages des personnages réalistes en 512 px dans persos-pck (scratchpad pack_reels.gd), affiches neons/realisations réduites à 512 px seulement sur iOS (main.neon_gallery_texture), image en résolution x1 sur iOS (index.html).
- 200 niveaux au lieu de 100 (levels.MAX_LEVEL). Supabase : supabase/niveaux200.sql à exécuter (contrainte niveau 1 à 200 sur la table joueurs).

## Version 1.86 (2026-10-22)
- La nuit, de vraies lampes au plafond éclairent chaque pièce des bâtiments (magasins, centres commerciaux, Marché Mondial, supermarché, armurerie ; dans les autres bâtiments, des lampes s'allument au plafond de la pièce où l'on se trouve). Murs et plafonds ne brillent plus.
- Technique : main.lit_interior + main.room_lights, nuit.gd (lampes OmniLight proches), bâtiments éclairés construits en morceaux de 24 m (main._fine / chunk_of) car le moteur limite les lumières par objet.
- La radio hip-hop démarre dès l'entrée dans le jeu.
- Correction : monter en passager dans la voiture ou l'hélico d'un autre joueur ne fait plus perdre de vie (sante._car_hits croyait que le véhicule nous renversait).

## Version 1.85 (2026-10-22)
- Trois méga-boss arbres vivants aux yeux rouges au sommet de la Vallée des Nuages (Vieux Chêne, Grand Saule, Pin Noir) : coups de branches, onde de choc, racines qui jaillissent ; 100 000 px, 2 Pixart, un objet rare et le coffre du méga-boss (vallee_arbres.gd).
- 160 monstres cubes du niveau 10 au 100, répartis également par niveau.
- Dans la vallée, animaux et monstres lâchent des objets communs ou moyennement rares ; les rares restent pour les boss et les coffres.
- Deux fois plus d'XP pour chaque niveau (niveau 100 deux fois plus dur).
- Statut GC (Game Creator) pour Lopo et Mike (codes GCLOPO et GCMIKE) : comme GM, en or plus brillant.

## Version 1.84 (2026-10-22)
- Nouvelle map « Vallée des Nuages » (porte A3 de l'aéroport, billet CR122) : montagnes dans les nuages, animaux à chasser, arbres fruitiers, lac avec pontons carrés et barques, monstres cubes aux yeux rouges du niveau 10 au 100.
- Deuxième monnaie Pixart (pièce d'or « pix$art », 10 Pixart = 1 $) gagnée dans les événements ou achetée dans la boutique Premium ; code ALAINPIXART.
- Bouton « Faire un don » dans Premium (PayPal), page de remerciement et 3 objets rares.
- Pièce de pixels noire avec le logo ; soldes Pixart et pixels empilés.
- Nouvelle disposition des boutons par défaut pour tout le monde (user://touches4.json).

## Version 1.83 (2026-10-22)
- Aéroport : le dallage du terminal était dessiné 12 cm au-dessus du sol où l'on marche ; les pieds ne s'enfoncent plus (airport.gd, aussi café et duty free).
- Plaque au-dessus des joueurs empilée sans chevauchement (plaques.layout) : de bas en haut étoiles, niveau et statut, pseudo, GM, Premium, badge.
- Pseudo, niveau et statut en police Lexend fine sans contour (fonts/Lexend.ttf) ; Premium -30 %.
- Barre de vie cachée, visible 6 s quand on touche un joueur (main._tap_health, Plaques.show_bar).
- 21 badges en deux styles au choix, Bijou ou Plat (badges/bijou, badges/plat), et effet du badge au choix : Particules, Aura (badge_aura.gd) ou Aucun.
- Étoiles de la note : blanc transparent, argent, or rose, or, diamant.
- Aura du personnage : voile lumineux qui monte des pieds, cercle au sol et étincelles (aura.gdshader, aura_sol.gdshader) au lieu de la bulle.

## Version 1.82 (2026-10-22)
- Véhicules plus réalistes (vehicles.gd : carrosseries lissées _loft/_smooth_body, vitres, montants, rétros, phares, jantes à rayons chromés).
- Pelouse réaliste (textures.gd _grass).
- Clans (clan.gd, supabase/clans.sql à exécuter) : nom, emblème, niveau, 30 membres maximum, chat du clan.
- Groupes de messages à plusieurs dans le téléphone (phone.gd, réseau).
- Code ALAIN100M réutilisable à volonté.
- Badges premium en relief et brillants (badges/*.png), étoiles au-dessus de la tête (etoiles.gdshader), pièce de pixels épaisse, police MSDF lisse pour les noms, noms des GM en or avec « GM » et arabesques (gm_nom.gd, gm_deco.gd, Cinzel).
- Ailes d'ange réalistes à plumes qui s'ouvrent et se ferment (ailes.gd, ailes_anim.gd).
- Émotions : « fumer » retiré, « dormir » et « macarena » ajoutées (les PNJ dansent la macarena au lieu de fumer).
- Style des personnages réalistes (reels_style.gd, onglet Apparence > Style) : couleur du t-shirt, couleur des cheveux, 13 coupes ; accessoires de tête adaptés à la taille de chaque tête (Objets.fit_reels + head_box).
- 33 quêtes avec PNJ donneurs, animaux et objets (quetes.gd, quetes_data.gd, tuile Quêtes).
- Centre équestre sur la plage sud-est (equestre.gd, cheval.gd) : 4 chevaux à acheter, montables, avancer, reculer, sauter.
- Le centre de l'IA (centre_ia.gd, livres_ia.gd, livre_ia_ui.gd, centre_ia_ecrans.gd) : tour de verre, 16 livres à feuilleter, PNJ, écrans géants, logos des IA, café.
- Boîte de nuit NOX (boite.gd) : façade taguée, bar, piste, DJ, VIP, toilettes, musique, PNJ qui dansent.
- Page d'accueil : nouveau montage vidéo 1080p (8 lieux) et vidéos des maps refaites.

## Version 1.81 (2026-10-21)
- Casino refait (casino.gd) : salle sombre, table de cuir avec tapis en dégradé, cartes arrondies avec coins et dos brodé, jetons de casino (piles), croupier et joueurs plus détaillés, roue de roulette réaliste, tapis de roulette en trois colonnes, machine à sous avec effet de cylindre.
- Mises au curseur (1 px jusqu'à tout ce qu'on possède) au blackjack, au poker (mise de départ et relance), à la roulette (valeur du jeton) et aux machines à sous ; boutons Min, ¼, ½, Max.
- Défenses de maison (defenses.gd, meubles « Pics de sécurité » 5 000 px et « Mitraillette automatique » 25 000 px, en mode Construire) : les pics sortent du sol et tuent sur le coup un joueur non invité ou un méchant, puis rentrent ; la mitraillette balaie un laser rouge, vise et tire sur les méchants et les joueurs non invités qui s'approchent (réseau « def » pour que les voisins voient les tirs).
- Le panneau SORTIE n'apparaît plus dans les maisons, seulement dans les lieux publics (main.is_private_home).

## Version 1.80 (2026-10-21)
- Hélicoptères refaits en Apache (vehicles.gd _heli) et changeables de couleur chez le concessionnaire (main.vehicle_color / set_vehicle_color, sauvegarde couleurs_vehicules, envoyé aux autres joueurs 'vc').
- Seuls les 20 personnages réalistes (reels.gd) restent au choix, avec portraits (persos/portrait_r*.png) ; anciens looks convertis (appearance.clean).
- 18 accessoires rares à trouver en objets lâchés (catégorie « porter » d'objets.gd : smartphone, montre, écouteurs, casquettes, bonnet, cowboy, ailes célestes, queues, oreilles, lunettes, moustaches, cravate), placés sur les os du personnage (Objets.fit_reels).
- Les pieds ne s'enfoncent plus jamais dans le sol (reels.gd Pilote.ground/_feet).
- Bug du bateau de croisière corrigé (nage coupée dans les zones).
- Gili n'attaque que si on l'attaque d'abord.

## Version 1.79 (2026-10-21)
- Boss moyen Gili (boss.gd) : perroquet gris qui vole, plonge et crie (sons/gili1-5.wav, enregistrement d'Alain), 12 000 PV, 120 000 px.
- Icônes d'armes réalistes (icones/arme_*.png, anciennes dans creator-docs/icones-armes-v1), images dans l'armurerie.
- Sac rangé par catégories (inventory.gd cat_of, pastilles Tout/Armes/Nourriture/Ressources/Tenues/Meubles/Rares/Objets).
- Sols, plafonds et toits durs à Paris, Tel Aviv, ferme et Battle Royale (_roof_collisions).
- On vole et on nage au-dessus de la mer jusqu'au bout de la carte (SEA_EDGE) ; Alcatraz reste fermée sans hélicoptère.
- Tel Aviv : entrée du Marché Mondial déplacée (ne chevauche plus le supermarché).

## Version 1.78 (2026-10-21)
- 20 personnages ultra réalistes (reels.gd, modèles Microsoft Rocketbox sous licence MIT) : Apparence > Personnage et habitants en civil. Sur le web, ils arrivent dans un second paquet (persos-pck.wasm) téléchargé pendant le jeu.
- Carte : tous les lieux avec nom et photo (parcs, salle de jeux, croisière, gare, studio, monuments de Paris et Tel Aviv, hôtels).
- Armurerie : curseur de 0 à 15 000 balles. Zone de combat : 240 zombies.
- Menu allégé (sans Agence, Boutique, Marché, Accès, Vocal, Téléphone, Carte, Cartes).

## Version 1.77 (2026-10-21)
- Carte identique dans toutes les villes (Paris, Tel Aviv, quartier des joueurs) avec filtres Tout, Bâtiments (nom + image), Joueurs, Monstres, Stations.
- Repère sur la carte (trait jaune + balise) et « Aller automatiquement ».
- Marchés visibles sur la carte, Marché Mondial transparent avec commerçants, panneaux Sortie et enseigne Entrée à l'aéroport.
- Échap ouvre le menu de tuiles (paramètres, apparence, sac, équipement, carte, cartes, guide, Débloquer).
- Cartes en plusieurs exemplaires (×N), message de drop en haut au centre.
- Enveloppe Messages en haut à droite (pastille + son), appels et vocaux retirés.
- Routes grises (brouillard corrigé), passagers moto 2 / hélico 4 / bateaux.
- Coffre et sac ouverts ensemble ; protection contre le vide (retour où on était + tuile Débloquer).

## Version 1.76 (2026-10-21)
- pets.gd _hostile : l'animal ne mord plus les voyous, boss et passants tranquilles (il les provoquait et les voyous attaquaient le joueur) ; il défend seulement contre ceux en mode attaque.

## Version 1.75 (2026-10-21)
- nuage.gd : sauvegarde en ligne (table Supabase « sauvegardes », supabase/sauvegardes.sql) de joueur.json, maison.json et telephone.json ; envoi 45 s après un changement ; à la connexion, la copie la plus récente gagne (récupération = relance de la partie) ; meta user://nuage.json {uid, t}.
- PC : à l'arrêt la souris ne tourne plus la caméra ; en avançant elle tourne gauche/droite et haut/bas (main._moving_keys).

## Version 1.74 (2026-10-21)
- classements.gd : tuile Classements (niveau, cartes, ennemis, maison, note) ; envoie ses chiffres à la table Supabase « joueurs » toutes les 5 min (account.push_stats) pour le site.
- voisins.gd : quartier des joueurs, un terrain par joueur, voir la maison des autres.
- premium.gd : packs de pixels et abonnements Argent/Or/Diamant (pas encore de paiement réel), badge PREMIUM brillant ; code PREMIUMTEST.
- Arme en main et tenue synchronisées ; molette = zoom ; message de faim ; amendes de traversée réparées ; boss passifs tant qu'on ne les attaque pas, ne traversent plus les murs, pas de laser à l'intérieur ; liste des boss et filtre monstres/stations sur la carte ; bouton GM « + Ajouter » dans l'inventaire.
- Site joueurs : https://haimassouline2011-jpg.github.io/creator/site/ (supabase/forum.sql et supabase/joueurs.sql).

## Version 1.73 (2026-10-21)
Marché Mondial et marchés de ville (ascenseur, étages, food court), 30 plats de restaurant (manger ou emporter), bus, métro et train avec arrêts, croisière à horaires partagés (piscine, casino, pêche, cabine), messages vocaux dans le téléphone (pastille rouge), éditeur visage/corps, boutons plus grands sur mobile, plein écran, onglet Nouveautés du guide.

## Version 1.72

- La police n'intervient plus quand on tire sans toucher personne, ni quand on abat un méchant (voyou, trafiquant, alien hostile, zombie, boss).
- Butin en coffres (butin.gd) : une carte ou un objet tombe dans un coffre en bois, en cuir, en or ou en diamant selon sa rareté. Il est à toi pendant 2 minutes, puis n'importe quel joueur peut l'ouvrir (les autres joueurs le voient).
- Les pixels d'un ennemi abattu tombent au sol en pièces à ramasser ; abattu depuis un hélicoptère, les pièces volent directement jusqu'à l'hélico.
- La tête (et un peu le buste) du personnage suit la souris ou le doigt : gauche, droite, haut, bas.

## Version 1.71 : cartes à collectionner et objets 3D
- **Cartes** (cartes.gd, dessins calculés par carte.gdshaderinc, aucune image) : 30 collections de 10 cartes (Feu, Eau, Plantes, Vent, Nuages, Lune, Soleil, Neige, Éclair, Étoiles, Volcan, Océan, Forêt, Désert, Aurore, Arc-en-ciel, Cristal, Montagne, Fleurs, Coraux, Tempête, Galaxie, Brume, Glace, Lave, Bambou, Cascade, Pluie, Sable, Comète). Cartes 1 à 6 communes, 7 à 9 rares, 10 légendaire. Un méchant abattu (voyou, fuyard, trafiquant, alien hostile, zombie) en a une fois sur 30, le boss toujours ; elle tourne par terre et se ramasse en passant dessus. Bouton « Cartes » en haut : album avec la grande carte qui tourne. Chaque collection complète donne un cadeau (pixels, arme rare, voiture/bateau/hélico, aimant, tissu rare).
- **Tissus rares** (Apparence > Vêtements) : Doré, Chrome, Néon, Diamant, gagnés avec les collections.
- **Objets 3D** (objets.gd) : un méchant en lâche un une fois sur 12. 10 objets de vitrine (trophée, œuf de dragon, crâne de cristal…) qui se posent avec Construire sur un socle sous cloche de verre, 10 objets à porter (couronne, ailes d'ange ou de démon, auréole, jetpack, épée dans le dos…) en les touchant dans le sac, 10 pierres précieuses à collectionner (les 10 = 60 000 px). Tout se vend au marché.
- Sons d'ambiance, vagues et grillons compressés (IMA-ADPCM, fichiers .import dans sons/) pour alléger la version web.

## Version 1.70 : gentils et méchants
- **Camps** (camps.gd) : quand on vise quelqu'un (à pied ou en hélico), il s'illumine et une étiquette apparaît : vert « Gentil » (passants, conducteurs, policiers), rouge « Méchant » (voyous, trafiquants, un alien sur deux, zombies, boss cyclope, bots du battle royale), jaune « Joueur ». Le réticule prend la même couleur.
- Dans la foule, un humain sur cinq est un trafiquant et un alien sur deux est hostile (foule._mechant) ; tirer sur un méchant n'est pas un délit.

## Version 1.69 : viseur de l'hélico et repères de construction
- **Viseur de l'hélicoptère** (explosifs.gd Sight) : croix au centre, cercle à l'endroit exact de l'impact avec la distance (jaune, rouge avec des coins quand une cible est accrochée) et anneau lumineux posé dans le décor.
- **Repères de construction** (reperes.gd) : grille du terrain, grille locale à la hauteur où l'on construit et cube fantôme vert (rouge si impossible) là où ira le prochain cube ; il suit la souris sur PC et le dernier endroit touché sur téléphone. En mode Détruire, le bloc visé est encadré en rouge.

## Version 1.68 : parachute et chutes
- **Parachute noir** (parachute.gd) : quand on tombe de plus de 2,5 m (toit, hélico…), Espace ou le bouton Sauter ouvre une voile noire qui freine la descente et permet de planer ; les autres joueurs la voient.
- **Dégâts de chute** : sans parachute, au-delà de 4 m on perd 5 points de vie par mètre (21 m = -85).

## Version 1.67 : personnages réalistes, motos, explosifs
- **Personnages réalistes** (realiste.gd, d'après l'image d'Alain) : corps sculpté d'un seul tenant, vrais yeux (iris, paupières), nez, oreilles, sourcils, lèvres, cheveux en volume, mains, vêtements superposés avec des plis. Tous les habitants l'utilisent, avec des tenues et accessoires variés (gen_realiste.py fait les textures).
- **Apparence** : « Réaliste » est le premier choix ; on change le corps (homme, femme), la barbe, la coiffure, le haut (veste et capuche, blouson, t-shirt, sweat, pull, chemise, costume, débardeur), la couleur du dessous, le bas (jean, pantalon, cargo, jogging, short, jupe), les chaussures (baskets, bottines, ville), la montre, le sac, les lunettes, le chapeau, le collier et les boucles.
- **5 motos** (onglet Motos du concessionnaire) : Éclair R1 sportive, Nero Roadster, Bison Chopper, Terra Cross, Dolce Scooter ; pilote à califourchon qui se penche dans les virages, batterie et usure comme les voitures.
- **Hélicoptère armé** : mitrailleuse (bouton maintenu, touche F) et missiles (bouton, touche G), visée au centre de l'écran.
- **Explosifs** (explosifs.gd) : grenade (lancée en cloche, rebondit), lance-roquettes RPG (moyen) et lance-missiles Titan (fort) à l'Armurerie ; explosion en zone, objets cassés, fumée.

## Version 1.66 : montre en languette
- La montre devient une petite languette bulle blanche en bas à droite (heure réelle, soleil ou lune et heure de la ville).

## Version 1.65 : ferme, murs, corps solides
- **Ma ferme** (bouton en haut à droite) : chaque joueur a un immense terrain avec une maisonnette, un puits, une forêt, une carrière (pierre, fer, or, diamant), un lac (pêche, sable) et un pâturage (vaches, moutons, poules). On récolte à la main : bois, pierre, eau, poissons, lait, laine, œufs, viande.
- **8 machines** (scierie, broyeur, foreuse, mine d'or, pompe, drague, pisciculture, élevage) à 6 niveaux : 200 000 / 400 000 / 800 000 / 1 600 000 / 3 200 000 / 6 400 000 px, de 0,5 à 16 ressources par minute, production même hors ligne (8 h de stock max).
- Construire utilise les matériaux du sac (bois, pierre, sable) au lieu des pixels quand on en a.
- **Murs** : habitants, voyous, policiers, zombies et boss contournent les bâtiments et ne tirent plus à travers. Caché dans un bâtiment hors de vue de la police, on la sème.
- **Corps solides** : on ne traverse plus les passants ni les voitures, les passants s'écartent entre eux.
- **XP de connexion** : 2 % d'un niveau par heure de jeu. **Police** : 2 fois moins de dégâts.

## Version 1.64 : code ALAIN100M
- Nouveau code propriétaire ALAIN100M = 100 000 000 px (Paramètres > Code propriétaire, une fois par téléphone).

## Version 1.63 : aliens et boss cyclope
- aliens.gd : un passant sur deux (foule._being, graine impaire) est un extraterrestre, 6 races (cinq_bras, deux_tetes, six_jambes, gris, cristal, tentacules), peau de couleur, combinaison brillante avec bandes lumineuses ; membres en plus accrochés aux pivots de jambes/bras.
- boss.gd (game.boss) : cyclope 3x (un œil au centre entouré de 14 dents, cornes), apparaît en ville toutes les 4-8 min (spawn), marche vers le joueur, coup de poing 22 PV de près, rayon de l'œil 12 PV de loin ; 3000 PV (Label3D), mort = 50 000 px + 2 armes rares parmi les 8 plus chères avec munitions + munitions de l'arme en main. Tirer dessus n'est pas un délit.
- Lampes de plafond des boutiques décollées du toit.

## Version 1.62 : combats de rue et police
- rue.gd (game.rue) : bandes de 2-3 voyous (capuche noire, casquette rouge) dans les villes, attaquent si on passe à moins de 10 m (AGGRO), tirer sur eux n'est pas un délit (legit/self_defense) ; un passant touché sort une arme 45 % du temps (foule etat "rue", riposte) ; niveau de recherche 1-5 étoiles (classe Stars en haut au centre), renforts police.add_reinforcement (voiture libre qui fonce vers le dernier endroit vu), agents qui descendent (police mode "intervention", rue.arrived) et tirent dès 2 étoiles (1 étoile : menottes au contact = amende), policier abattu = +1 étoile ; semer la police = 25 s sans être vu (ligne de vue, 75 m) ; K.O. recherché = arrestation (Alcatraz dès 2 étoiles, sante._to_hospital -> rue.on_ko) ; plus de téléportation de la patrouille au bout de 15 s.
- Courses-poursuites : toutes les 70-120 s, un coupé noir de voyous file autour d'un pâté de maisons avec la police derrière ; abattre le fuyard = +400 px.
- Plafonds : lampes de plafond des immeubles habitables (tours.hints, tours._build_floor) décollées de la dalle (rayures sur mobile).

## Version 1.61 : réticule sans viser
- combat._hip_point : dès qu'une arme est en main, le réticule est affiché là où partira le tir (cible verrouillée par la visée auto, en rouge, sinon 18 m devant), Crosshair.at/use_at.

## Version 1.60 : viseur façon FPS
- combat.gd : zoom de visée en douceur (fov_target), réticule dynamique (s'écarte en bougeant et en tirant, rouge sur une cible), dispersion (bloom) et recul (pitch remonte puis revient), X de touche (rouge si la cible tombe) avec petit son, lunette de sniper plein écran (classe Scope, caméra aux yeux, fov 12). En visée, la balle va sur la cible sous le réticule et la caméra tourne moins vite (sensibilité × fov/45).
- Rayures au sol : camera.near 0.15 (au lieu de 0.05) ; à Tel Aviv, boulevard Rothschild, place Dizengoff et Jaffa surélevés au-dessus des trottoirs.

## Version 1.59 : correctifs Tel Aviv
- Rayures sur le sol : le sable de la plage passait sous l'asphalte de la ville (deux sols à la même hauteur). Le sable s'arrête maintenant à x = -112.
- Planchers durs : chaque étage des immeubles Bauhaus, des tours et des tours Azrieli a une collision.

## Version 1.58 : la foule des villes
- foule.gd : à Hong Kong, Paris et Tel Aviv, 40 à 46 passants font le tour des pâtés de maisons autour du joueur (recyclés vers les quartiers proches quand ils sont à plus de 100 m), s'arrêtent aux vitrines et repartent avec un sac, téléphonent en marchant ou arrêtés, fument, écoutent de la musique ; groupes de 2 ou 3 qui discutent ; 14 à 22 personnes assises sur les bancs et aux terrasses (loisirs.seats, paris.seats) ; à Paris et Tel Aviv, 12 voitures avec conducteur tournent autour des quartiers (freinent et klaxonnent devant le joueur). Passants touchés par balle : chute, pixels (combat.loot), retour après 40 s.
- paris.blocks et telaviv.blocks : trottoirs des pâtés de maisons.

## Version 1.57 : Tel Aviv réaliste
- tours.gd : immeubles et tours habitables. Porte « Entrer » ou ascenseur, liste des étages (choix.gd), l'étage choisi est construit à la demande : bureaux (postes, écrans, salle de réunion, employés assis, logo d'entreprise), deux appartements meublés par étage (salon, cuisine, chambre, sièges), observatoire au sommet de la tour ronde. Murs de verre invisibles, on voit la ville.
- telaviv.gd : ville blanche refaite, immeubles Bauhaus de 3 à 5 étages et tours de 12 à 22 étages, tous habitables, vitres légèrement transparentes (GLASS alpha 0.38) avec pièces éclairées derrière (tours.hints, cachées pendant la visite via group_mm).
- Azrieli : centre commercial creux de 90 x 60 m, 12 m sous plafond (8 boutiques dont Super-Pharm, Neon Israel, Home Center qui vendent des objets, magasins de mode qui ouvrent l'Apparence), aire de restauration (4 comptoirs, tables avec clients assis), galerie haute, escalators, 14 promeneurs. Trois tours de verre (ronde 21 étages, triangulaire 19, carrée 17), bureaux puis appartements, ascenseur au pied de chaque tour.
- hotels.gd build_telaviv : 3 hôtels du front de mer (Dan, Royal Beach, Hilton), 24 étages. casino.gd (at, sub_name) : casino Tel Aviv Royale sur l'îlot (146, 114).

## Version 1.56 : Zone de combat et de drop
- zombies.gd : île géante au sud-ouest (ISLAND x -470..50, z 470..930), pont rouillé sur la rue x = -209 depuis la plage sud, ruines, carcasses, tonneaux en feu, croix DROP.
- La nuit (night_amount > 0,45) : jusqu'à 24 zombies petits / moyens / grands qui sortent de terre, chassent le joueur et mordent (6 / 12 / 25 de vie). Abattus : 30 à 500 px et 15 à 60 XP combat, pas de délit. Écrasés par une voiture lancée.
- 12 caisses dans les ruines (px ou nourriture/potions, reviennent après 3 min) et largage en parachute la nuit (500 à 2500 px + super potion).

## Version 1.55 : appels entre joueurs
- Android : le micro est demandé dès le lancement et rouvert quand l'autorisation arrive (voice.gd _on_permission) ; avant, un micro ouvert sans autorisation restait muet.
- Écran d'appel : diagnostic en direct (« Ton micro capte ta voix / ne capte rien », « Sa voix arrive / n'arrive pas »), net.gd v_mic/v_recv ; voix de l'appel plus forte (+8 dB).

## Version 1.54 : piscines, détente, Paris résidentiel, chats, conducteurs et aménagement du magasin
- **Piscines** (loisirs.gd) : on entre et on nage dans les piscines des villas, des hôtels et de Paris ; on s'assoit sur les chaises, on s'allonge sur les lits, transats et canapés (au choix).
- **Paris** (paris_immo.gd) : quartier haussmannien au sud (appartements à acheter ou louer) et 10 villas de luxe avec piscine, agence Paris Prestige.
- **Chats des rues** (chats.gd) à Hong Kong et à Paris, on peut les caresser.
- **Conducteurs** (civils.gd) : 12 voitures avec un habitant au volant ; on peut les abattre, la voiture s'arrête et on fouille ses poches (50 à 2500 px, combat.loot), les passants aussi. Les passants s'arrêtent pour fumer, écouter de la musique ou danser.
- **Aménager mon magasin** (amenagement.gd) : dans son magasin du marché, ajouter, déplacer, tourner, retirer 13 sortes de meubles (40 max), cadres, écran géant et chevalet avec ses photos, vider ou remettre le décor d'origine (bloc caché avec main._conceal).

## Version 1.53 : studio d'enregistrement, enseignes 3D, Neon Israel et personnages réalistes
- Creator Studio (studio.gd, Néo-Cité REC (-560,0,60)) : cabine vitrée avec micro, table de mixage, mur des disques d'or. 3 instrus originales (gen_instrus.py -> sons/instru_*.wav), enregistrement jusqu'à 60 s par le bus « Micro » (voice.gd), voix ramenée à 16 kHz et mixée avec l'instru. Coach IA hors ligne (hauteur par autocorrélation : justesse dans la gamme, stabilité, volume, présence, conseils). Bibliothèque sauvée sous « studio », sons dans user://studio/<id>.pcm (restent sur l'appareil). Presser 10 disques = 40 px (objet « disque:<id>:<titre> », vendable au marché ou au label).
- Entrée des boutiques partenaires : choix « boutique virtuelle » ou « site » (choix.gd). Neon Israel : 6 néons 3D en vente (dans le jeu, en vrai ou les deux), borne « Crée ton néon ».
- Pubs géantes Neon Israel (pub_neon.gd) sur des tours de Hong Kong et Tel Aviv : logo blanc et diaporama des réalisations.
- Toutes les enseignes en vraies lettres 3D (main._channel_sign : corps, face lumineuse ou rétroéclairée, halo).
- Paris et Tel Aviv ont les mêmes magasins que Hong Kong (main._city_shops : marché, armurerie, supermarché).
- Personnages et PNJ réalistes (gen_visages.py, Persos.npc).

## Version 1.52 : animaux de compagnie, Tel Aviv et nouvelle icône
- Animalerie sur la plage ouest (pets.gd, SHOP (-282,0,34)) : chat, chien, perroquet, singe, serpent (2000 à 4000 px). L'animal suit le joueur, attaque pendant 15 s celui qui nous frappe (ou les bots du battle royale) ; les autres joueurs le voient (champ « pt » du message de position). Sauvegarde « animaux ».
- Tel Aviv (telaviv.gd, ORIGIN (0,0,-6000), porte A5 de l'aéroport au lieu de Londres, billet 80 px) : plage avec maîtres-nageurs, parasols, volley et lettres TEL AVIV, promenade bordée de palmiers, 5 restaurants de plage où l'on mange (houmous, falafel, shakshuka, sushi, café : pixels contre faim), hôtels du front de mer, Ville blanche Bauhaus, boulevard Rothschild, place Dizengoff, tours Azrieli, vieux Jaffa et son horloge. Les passants parlent hébreu (voix.gd « he »). Comptoir Creator Air pour le vol retour.
- Icône de l'appli : logo Creator noir dans un cercle blanc (icon.png, ui/icone-*.png).

## Version 1.51 : étoiles, Néo-Cité, voix des habitants et émotions
- Note sociale (notes.gd) : on note un joueur de 1 à 5 étoiles dans son profil ; étoiles au-dessus de la tête (plaques.set_stars, etoiles.gdshader : noires < 3, métal 3–4,5, arc-en-ciel ≥ 4,5). Classement du jour payé à la première connexion du lendemain (5000/3000/1000/200/50/50 px, 3 votes mini), depuis la table Supabase « notes », sinon les joueurs croisés.
- Néo-Cité (neocite.gd) : île à l'ouest (x -850..-450) reliée par un pont de verre sur la rue z=-5 ; tour torsadée, biodôme, Habitat 2077, soucoupes, tour en spirale, monorail, hologramme, atelier des architectes (PNJ créés à l'approche).
- Voix des habitants (voix.gd) : tout PNJ de npcs._person est dans le groupe « pnj » ; à 3 m il salue dans la langue du lieu (cantonais, français, anglais) avec une bulle et la synthèse vocale (project.godot audio/general/text_to_speech). Police hk-chinois.ttf refaite avec ces caractères.
- Bouton Émotion (emotes.gd) : danser, sauter de joie, yoga, cigarette, musique ; vu par les autres joueurs (champ « em » du message pos).

## Version 1.50 : barre d'état, profils, signalement, revente et guide
- Barre en haut à droite (levels.gd Badge) : vie, faim et XP ; la faim (sante.gd) baisse en 2 h, plus vite en courant ou nageant ; à 0 on perd de la vie.
- Profil d'un joueur (profil.gd) : toucher un joueur ; amis, échange d'objets, message, signaler.
- Signaler (signaler.gd) : motif, description, 3 captures ; envoyé dans la table Supabase « signalements », gardé sur le téléphone tant qu'elle n'existe pas.
- Revente : véhicules (dealer.gd) et maisons (realestate.gd) au prix d'achat −10 % (main.RESALE), ou au marché à prix libre (objets « veh:<id> » et « maison:<id> »).
- Bouton « Guide » (guide.gd) à droite du Téléphone, 8 onglets ; s'ouvre tout seul à la première partie.

## Version 1.49 : Creator Marine, la boutique de bateaux
- Pavillon de verre sur la plage sud (marine.gd, à 70 m à l'ouest du centre) : podiums avec modèles exposés, vendeur, comptoir « Creator Marine · bateaux » qui ouvre l'onglet Bateaux du concessionnaire (dealer.gd, achat seulement à la marina).
- Ponton en T avec bornes de recharge vertes (« Recharger le bateau », même borne que les voitures : 2 px/kWh) et bateaux d'exposition amarrés qui bercent.
- 15 modèles (bateaux.gd, vraies coques en V) : Skate des mers (foil), Paddle électrique, Jet-ski Vague et Turbo, Zodiac, bateau de pêche, Riva, Cigarette Racer, voilier, catamaran, Yacht Azur, Méga-yacht Creator (héliport, jacuzzi), Dauphin, Requin blanc, Orque.
- Navigation (main._sail) : flotte, tangue, lève le nez, sillage d'écume, s'arrête au bord (plage, pontons, îles) ; jusqu'à 380 m au large. Les animaux n'ont pas de batterie et battent de la queue. « Naviguer » met le bateau à l'eau à côté de toi ou à la marina ; « Descendre » près d'un ponton ou de la plage te pose à terre, sinon tu plonges.

## Version 1.48 : correctif du battle royale, version Mac
Version Mac : preset "macOS" (Creator.app universelle Intel + Apple Silicon, signature ad hoc, non notarisée : la première fois, Réglages Système > Confidentialité et sécurité > Ouvrir quand même).
Au saut de l'avion, la caméra restait bloquée au bord de la ville de Hong Kong alors que le personnage était déjà sur l'île : on voyait le vide. La caméra suit maintenant directement le joueur jusqu'à l'île (royale.gd _camera, start, in_zone, clamp_zone).

## Version 1.47 : écran géant dans Neon Israel

- Écran géant de 6,4 x 3,6 m sur le mur de droite de la boutique Neon Israel. Il passe en boucle 6 animations de néons de 7 secondes : le logo Neon Israel qui s'allume, un cœur qui se dessine avec « love », OPEN lettre par lettre, un soleil rétro avec un sol quadrillé, un éclair avec des ondes, une fleur d'anneaux arc-en-ciel.
- Les animations sont dessinées par un shader (neon_ecran.gdshader) : nettes en HD à toutes les distances, sans fichier vidéo à télécharger. L'écran éclaire la boutique en rose violet.

## Version 1.46 : battle royale, pièces x3, une fenêtre à la fois

- Battle royale (royale.gd) : borne orange devant l'aéroport, inscription 50 px. On saute d'un avion au-dessus de l'Île Royale (île à part, loin à l'ouest), parachute qui s'ouvre à 50 m, 15 adversaires automatiques, caisses jaunes (armes, armure +50, soins +40, balles), zone violette qui se resserre en 5 étapes et fait perdre de la vie dehors. Le dernier survivant gagne 2 500 px. Les armes de la partie sont à part : on retrouve les siennes à la fin.
- 3 fois plus de pièces dans les rues (450) et plus aucun autre objet à ramasser.
- Une seule fenêtre à la fois : en ouvrir une ferme les autres (main._one_window), pour qu'elles ne se chevauchent plus.

## Version 1.45 : voitures électriques à 4 places

- Carrosserie vernie et brillante, liserés et calandre chromés, feux LED avec barre lumineuse arrière, pare-chocs, poignées et joints de portes.
- 4 places dans chaque voiture : 4 sièges baquets, tableau de bord avec écran et volant. Le conducteur est assis au volant, visible à travers les vitres.
- Passagers : près de la voiture d'un autre joueur, "Monter en passager" t'assoit à une place libre (3 passagers maximum). "Descendre" ou Espace pour sortir.
- Toutes les voitures sont électriques : la station-essence devient une station de recharge (bornes vertes, 2 px le kWh, batterie de 75 kWh, recharge +25 % ou complète).
- Les chocs abîment les voitures 5 fois moins vite.

## Version 1.44 : casino Creator Royal

- Casino géant en Hong Kong (quartier sud-ouest, enseigne néon "CASINO"), visible sur la carte.
- Roulette européenne (rouge/noir, pair/impair, douzaines, numéros plein x36), blackjack (sabot de 6 jeux, doubler, blackjack payé 3:2), poker Texas Hold'em et machines à sous (20 % de parties gagnantes, gains x2 à x100).
- S'asseoir à une table ouvre le jeu en plein écran avec le croupier et les autres joueurs autour (pour l'instant des joueurs automatiques), mises en pixels, bouton "Quitter la table" ou Échap.
- Caisse et personnel (croupiers, hôtesse).

## Version 1.43 : 10 hôtels géants

- hotels.gd : 5 tours-hôtels de 28 étages à Hong Kong (terrains (3,-1), (-3,1), (3,3), (-3,-3), (0,4)) et 5 palaces de 7 étages à Paris, chacun sur un pâté de maisons (Concorde, Rivoli, Lumière, Saint-Germain, Belle Époque). Noms dorés sur la carte.
- Rez-de-chaussée : grand hall en marbre avec réception, réceptionnistes et voiturier, deux ascenseurs dorés, restaurant (buffet 40 px, santé au maximum) et salle de jeux (billard, ping-pong, bornes d'arcade, tapis de course, petits gains en pixels).
- Toit : piscine avec marches, transats, parasols, bar à cocktails (15 px, +25 santé), barman et maître-nageuse.
- Réception : louer une chambre (500 px pour 7 jours, prolongeable) ou visiter la chambre témoin. La chambre, en haut de la tour, a deux murs vitrés sur la ville, un grand lit, une salle de bains et un coffre-fort qui garde les ressources et les meubles rares du sac. Sauvegarde « hotels ».
- Le personnel apparaît à la première approche ; la chambre est construite à la demande et rangée quand on la quitte.

## Version 1.42 : chasse aux pigeons

- 12 groupes de pigeons (pigeons.gd) : la ferme, la plage tout autour de la ville, devant l'aéroport, et à Paris au Champ de Mars et aux Tuileries. Ils marchent, picorent, roucoulent et s'envolent si on court vers eux, si on passe en voiture ou si on tire près d'eux, puis reviennent se poser.
- Nouveau **Fusil de chasse** à l'armurerie (6 000 px, 2 cartouches, portée 60 m). Au fusil de chasse ou au fusil de précision, un pigeon touché tombe en plumes ; on marche dessus pour ramasser la **viande de pigeon** (sac à dos) : elle se mange (+15 santé) ou se vend 15 px. +15 XP « Chasse » par pigeon.
- Chasser n'est pas un délit : la police ne vient pas pour un tir au fusil de chasse ou un tir qui touche un pigeon. Un pigeon abattu est remplacé au bout d'une minute.
- Sons d'envol et de roucoulement (gen_sons.py pigeons), icône de la viande (gen_icones.py).

## Version 1.41 : maisons plus grandes, appartements, vraie tour Eiffel

- Maisons (main._neighbour_house, aussi les villas de l'agence) : environ 19 x 12 m au sol au lieu de 13 x 8, 3,6 m sous plafond, trois niveaux (rez-de-chaussée, étage avec chambre et coin salon, dernier étage en retrait avec chambre et grande terrasse), deuxième escalier. villas[i]["w"] et ["haut"] servent aux décors de realestate.gd.
- Villa Creator : 12 m de profondeur, un étage complet (chambre, salon) et le toit-terrasse au-dessus.
- Appartements de Paris (appartements.gd) : 2 grands appartements par étage au lieu de 4, sur toute la profondeur (côté rue : salon, chambre, cuisine, salle de bain ; côté cour : chambre d'enfant, salle à manger avec piano, chambre parentale). Immeubles habitables à 3,8 m par étage.
- Tour Eiffel (paris._eiffel) refaite à 70 % de la vraie : 87 m de base, courbe de la vraie tour (_eiffel_w), quatre piliers en treillis, grands arcs, 1er étage en anneau avec frise à arcades et pavillons vitrés, 2e étage à 80 m, fût unique jusqu'au sommet à 193 m, campanile et antenne. La nuit : dorée, et elle scintille les 5 premières minutes de chaque heure du jeu (paris.sparkle).
- Alcatraz : une tâche toutes les 6 min (environ 2 h pour 100 points, comme demandé).

## Version 1.40 : prison Alcatraz by Creator

- alcatraz.gd : île au nord de la ville (ISLAND autour de x 12, z -475), seulement en hélicoptère (alcatraz.allowed : à la nage on reste bloqué au large).
- Enceinte de 5 m avec barbelés et porte fermée, 4 miradors avec sniper et projecteur la nuit, bloc de 10 cellules (lit, toilettes, barreaux), infirmerie, cour avec terrain de basket, atelier, héliport, guichet, phare.
- La police envoie en prison les crimes graves (Agression armée, Coup de feu) au lieu de l'amende : transfert, tenue orange (look["prison"], aussi vue par les autres joueurs), pas d'armes.
- Travaux : 3 tas à nettoyer dans la cour et 3 murs à monter à l'atelier, 8 s de travail sur place, +5 points, une tâche toutes les 6 min (environ 2 h en tout). 100 points = libéré. Ou caution de 15 000 px au bureau du directeur.
- Évasion par les caisses empilées contre le mur est : dehors, les snipers tirent (34 de dégâts), K.O. = réveil à l'infirmerie de la prison.
- État sauvegardé ("prison"), île et nom sur la mini-carte.

## Version 1.39 : arbres, herbe et fruits réalistes

- nature.gd : arbres feuillus en cartes de feuilles, palmiers à palmes arquées, touffes d'herbe ; tout bouge au vent (shader WIND).
- Textures dessinées par gen_nature.py (nature/*.png).
- Remplace les arbres en cubes de la forêt, de l'aéroport et de Paris, et tous les palmiers (plage, digue, aéroport).
- Herbe sur la forêt, les pelouses de l'aéroport et les jardins de Paris (cases de 24 m, visibles à 34 m).
- Verger dans les deux rangées du fond de la forêt : pommier, oranger, cerisier, pêcher, manguier. « Cueillir » donne un fruit (ressource), qui se mange dans le sac pour rendre de la vie ; un fruit repousse toutes les 25 s.
- Icônes des fruits dans gen_icones.py. Aperçu : apercu-nature.png.

## Version 1.38 : 21 personnages manga

- persos.gd : les 21 personnages de l'image d'Alain (10 filles, 11 garçons), corps lisse, vêtements de chacun, cheveux en mèches.
- Visages dessinés par gen_visages.py (persos/visage_<id>.png), portraits des cartes dans persos/portrait_<id>.png (rendus dans le jeu).
- Marche réaliste : genoux et coudes qui plient, buste qui balance ; les mèches bougent avec la vitesse, les virages, les pas et le vent.
- Apparence > Personnage : grille des 21 personnages, et « Mon style » pour le personnage fait main. Toucher un autre onglet repasse en « Mon style ».
- Les anciennes parties reçoivent un personnage au hasard, à changer dans Apparence.
- Échap ferme ce qui est ouvert (fenêtre, chat, téléphone, radio, barre d'armes, arme en main, construction) ; s'il n'y a rien d'ouvert, il ouvre le menu.
- Aperçus : apercu-personnages.png, apercu-choix-personnage.png.

## Version 1.37 : galerie Neon Israel modifiable

- Dans la page Marché de Neon Israel, le propriétaire voit toute la galerie en vignettes numérotées.
- Toucher une image la sélectionne : « ◀ Avant » et « Après ▶ » la déplacent, « Supprimer » l'enlève.
- « Ajouter une photo » ajoute une photo du téléphone (30 images maximum), « Galerie d'origine » remet les 20 photos de départ.
- Le mur gauche de la boutique se reconstruit tout de suite (sauvegarde « galerie_neon », reprend les photos de la 1.36).
- Aperçu : apercu-galerie-editeur.png.

## Version 1.36 : galerie Neon Israel, la boutique d'Alain

- 20 photos de réalisations Neon Israel (envoyées par Alain, neons/realisations/r01-r20.jpg, originaux dans uploads/neon-israel/realisations) encadrées en deux rangées sur le mur gauche du showroom (neon_israel.rebuild_gallery).
- Neon Israel est la boutique du propriétaire : sur un appareil où un code propriétaire a été entré (ou le nouveau code NEONISRAEL, 0 px), la page Marché de Neon Israel montre « Ma boutique Neon Israel » avec « Ajouter une photo » (10 au plus, gardées sur l'appareil, sauvegarde "photos_neon") et « Retirer mes photos ». Elles s'ajoutent à la galerie.

## Version 1.35 : vrai logo Neon Israel

- Le logo rond d'Alain (neons/logo.png, original dans uploads/neon-israel/logo-original.png) en grand caisson lumineux rond au-dessus de l'entrée, et en petit au mur du fond (neon_israel._round_lightbox).

## Version 1.34 : architecte IA, magasins géants, caisson Neon Israel

- Architecte IA (architecte.gd, bouton « Architecte IA » en mode Construire) : on écrit une phrase (FR/EN/HE) et le bâtiment se construit bloc par bloc sur son terrain. Comprend maison, villa, cabane, tour/immeuble, château, pyramide, phare, temple ; nombre d'étages ; petit/grand/géant ou « 10x12 » ; matériau ou couleur (bois, brique/rouge, pierre/gris, verre, blanc/moderne) ; toit plat ou pointu ; piscine, jardin, meubles. Aperçu du nombre d'éléments et du prix avant de construire. Fonctionne sans connexion (pas un vrai modèle d'IA en ligne).
- Deux magasins géants à louer (5 fois un grand : 450 places, 5000 px), de part et d'autre de Neon Israel (MEGA_PLOTS), sur la carte.
- Fermer son magasin (Marché > Mon magasin > Fermer mon magasin, deux touchers) : tous les objets en vente reviennent dans le sac.
- Raccourcis PC : M ouvre ou ferme la grande carte, T ouvre ou ferme le téléphone.
- Neon Israel : grand caisson lumineux à l'entrée, face blanche éclairée et nom en noir. Pour mettre le vrai logo : déposer l'image dans neons/logo.png.

## Version 1.33 : radio de musique libre

- Bouton casque en bas à droite (radio.gd, déplaçable) : stations Pop, Dance, Hip-hop, Chill ou l'ambiance du jeu, bouton « Morceau suivant ». Morceaux libres de Jamendo, les plus écoutés de la semaine par style (identifiant d'application JAMENDO_ID dans radio.gd). Chaque morceau est téléchargé puis joué, le suivant se prépare pendant l'écoute ; la musique d'ambiance se tait pendant la radio. Le choix de station est gardé. Réglages Son et volume Musique s'appliquent aussi à la radio.

## Version 1.32 : images de l'inventaire, carte plus complète

- Chaque objet du sac a sa petite image : bûches de bois, bloc de pierre, cristal, poissons, lingots, fruits, potions, néons, meubles rares et la silhouette de chaque arme (pistolet, revolver, fusil, sniper...). Images dans icones/, dessinées par gen_icones.py (relancer après un nouvel objet) ; sans image, la case garde le cube coloré.
- La carte montre l'île de l'aéroport (terminal, piste, pont), l'étiquette « Aéroport » et la « Zone de pêche » ; en zoomant sur la grande carte, le nom de chaque boutique du marché apparaît.

## Version 1.31 : showroom Neon Israel, aurores boréales

- neon_israel.gd : le vrai atelier Neon Israel en grand showroom (22 x 18 m) sur son propre terrain (0, -3), au nord du marché, d'après la photo d'Alain : murs clairs, parquet, rails de spots, baie sombre, bureaux blancs avec écrans, étagère de figurines, comptoir avec vendeuse, 4 lumières chaudes. Néons dessinés en images (neons/*.png, faits par gen_neons.py) : Einstein, fleurs arc-en-ciel, fusées, cœur, barres, « Let's Create », « OPEN ». Grande enseigne rose sur le toit. C'est la 31e entrée de `shops` (partenaire) ; boutiques.PARTNERS est vide et la boutique 5 redevient normale.
- sky.gdshader : aurores boréales la nuit (deux rideaux vert et violet qui ondulent).
- Le bouton Arme se retraduit quand la langue change.

## Version 1.30 : vrais commerces, objet Image

- boutiques.PARTNERS : vrais commerces partenaires (n° de boutique au marché -> nom, métier, site, articles). Le premier : Neon Israel (boutique 5, métier "neon", décor _neon avec enseignes Label3D lumineuses), qui vend 6 néons (RARE neon_*, enseigne_led). Dès qu'on entre, le bouton « Visiter le site … » ouvre le vrai site (OS.shell_open). Les boutiques partenaires ignorent la sauvegarde du marché.
- images.gd : choisir une photo sur l'appareil (web : input file JS ; PC : dialogue natif ; Android : FileDialog), réduite à 512 px dans user://images/<id>.png.
- Objet « Image » en mode Construire (FURNITURE "image") : on choisit la photo puis on touche où la poser ; bloc "image:<id>:<quart de tour>" (main._image_block, cadre doré).
- Mon magasin > Ma vraie boutique : jusqu'à 6 photos accrochées aux murs (main._shop_decor) et le site internet du commerce (bouton à l'entrée). Sauvegardés dans "marche" (photos, site). Pas encore partagés avec les autres joueurs : il faudra un stockage en ligne.

## Version 1.29 : vie, combat, route de l'aéroport, mode solo

- sante.gd : 100 points de vie (pastille sous Niveau, barre sur la plaque de chaque joueur et passant). Balles : 10 tirs de petit pistolet, 3 de fusil à pompe, 1 de précision (sante.DAMAGE). Une voiture qui nous renverse fait perdre de la vie. À 0 : K.O., réveil soigné à l'hôpital.
- Soins : potions et nourriture (pomme, sandwich, nouilles, potion, super potion) à l'épicerie ; poissons et récoltes se mangent (fiche Niveau > Ressources, bouton Manger) ; un clic sur un objet du sac l'utilise.
- Clavier/souris : Échap ouvre/ferme le menu, I l'inventaire, clic gauche tire avec une arme, clic droit maintenu = viseur (tir au centre de l'écran). Sur mobile : bouton Viser.
- Les tirs entre joueurs passent par net.gd (événement "touche"), la vie est envoyée avec la position ("h").
- Route de l'aéroport : dalles abaissées au niveau de la ville (plus de marche à x=272 qui bloquait la voiture), limite de conduite corrigée.
- account.gd : bouton « Jouer en solo, sans compte » quand le serveur est injoignable (toujours visible en version web : la page claude.ai bloque les connexions extérieures).

## Version 1.28 : touche Entrée pour le chat
- Sur PC, Entrée ouvre le chat et met le curseur dans le champ (main._unhandled_input, chat.open_typing) ; Entrée envoie le message et rend la main au jeu.

## Version 1.27 : badges animés, personnel des magasins, grande route de l'aéroport
- Barre des armes (combat.gd) : le bouton Arme ouvre en bas toutes les armes ; celles qu'on a sont colorées (vert, bleu, orange selon le prix), les autres en gris avec leur prix à l'Armurerie. On touche une arme pour la prendre.
- Plaque au-dessus de chaque joueur (plaques.gd) : badge animé, pseudo, « Nv 12 · Statut ». 14 statuts et 8 badges (feu, eau, feuilles, plume, vent, soleil, lune, pluie) dont les pixels volent (CPUParticles3D). Choix dans la fiche Niveau (badge en haut à gauche), sauvegardé dans « progression » (statut, badge) et envoyé aux autres joueurs dans « bonjour » (lv, st, bd).
- Personnel (boutiques.gd setup_staff/update) : un vendeur derrière le comptoir de chaque boutique ; au supermarché 3 caissières, 2 employés qui marchent dans les rayons, un primeur, l'accueil. Ils disent bonjour et se tournent vers le joueur à moins de 3,5 m.
- Grande route de l'aéroport (airport._causeway, CAUSEWAY élargie à 28 m depuis x = 272) : 2 × 2 voies, terre-plein central avec palmiers et lampadaires doubles, trottoirs bordés de palmiers et de lampadaires, garde-corps vitrés seulement au-dessus de la mer. Les parasols de la plage évitent la route.
- Hong Kong (hongkong.gd animate) : une enseigne sur cinq est en panne (grésille, s'éteint par moments) ; écrans publicitaires géants sur les façades (ADS : nouilles, films, armurerie, jeux, Creator Air…) qui défilent toutes les 4 s avec un flash.
- Construction : le rayon du clic ignore notre propre personnage (avant, cliquer juste devant soi disait « Pas assez de place »). Le clic droit est resté comme avant (caméra), à la demande d'Alain.

## Version 1.26 : quartier commerçant moderne, ville vue de l'intérieur, aimant

- **Par les fenêtres, on voit la ville** : le mode intérieur garde la caméra dans le bâtiment (6 m au plus) mais ne cache plus le dehors. La lumière ambiante est relevée à l'intérieur (`interieur.gd`, `glow`).
- **30 boutiques au lieu de 15** (`MARKET_PLOTS`, 6 terrains ; les 3 premiers gardent leur ordre pour les sauvegardes), plus grandes (7×7, 9×8, 12×9 m) et modernes (`boutiques.gd`) : vitrine du sol au plafond, porte vitrée, comptoir au fond, enseigne lumineuse « Métier · propriétaire ». Six métiers en alternance : bijouterie de luxe, fleuriste, mode, maison & déco, high-tech, épicerie fine. Les articles suivent le métier.
- **Supermarché** (`SUPERMARKET_PLOT` (2, -2)) : halle vitrée, six rayons garnis, frigos, fruits et légumes, trois caisses avec caissières, chariots.
- **Agence immobilière** refaite (`realestate._agency`) : cube de verre de 7 m de haut, mezzanine, accueil et écrans géants, bureaux des conseillers, maquettes des six villas sous verre, salon d'attente, parvis.
- **Aimant** (objet rare, 300 px, Boutique et magasins high-tech) : tant qu'il est dans le sac, les pièces à moins de 15 m filent vers le joueur (`MAGNET_RANGE`, `_update_pickups`).

## Version 1.25 : les immeubles de Paris sont habitables

- Chaque immeuble haussmannien (137 en tout ; Louvre, Grand et Petit Palais, Crillon exceptés) est creux, avec des vitres claires (`paris.gd`, couleur `GLASS`) : de la rue on voit les pièces, de chez soi on voit Paris.
- Porte cochère ouverte avec numéro de rue, hall en marbre avec tapis rouge, boîtes aux lettres et ascenseur doré (`paris._habitable`).
- L'ascenseur dessert 7 étages de 4 appartements meublés (salon avec cheminée, canapé, salle à manger, chambre, cuisine, salle de bain), construits seulement quand on y monte (`appartements.gd`). Chaque porte porte le numéro et le nom de l'habitant, certains sont « À louer ».
- **Mode intérieur, pour tous les bâtiments** (`interieur.gd`) : dès qu'on entre (un plafond au-dessus de la tête et des murs presque tout autour), une coque claire entoure le bâtiment juste derrière ses murs. Par les fenêtres et les portes on ne voit plus la ville ni les gens dehors, seulement la lumière du jour (ou la nuit). La caméra se rapproche (6 m au plus) et reste dans le bâtiment. Marche pour les magasins, l'agence, l'hôpital, l'aéroport, les maisons et les immeubles de Paris.
- **Visite facile à Paris** : « Entrer · adresse » devant chaque porte cochère ouvre directement l'ascenseur ; à chaque étage, un plan en haut à droite liste les 4 appartements (numéro et nom) : un bouton et on est au milieu du salon.

## Version 1.24 : billets d'avion et Paris

- **Employés Creator Air** (airport.gd `_agent`) : 24 employés en uniforme bleu marine, foulard aux couleurs du comptoir, badge et casquette dorés, derrière les guichets d'enregistrement (3 par côté de chaque îlot, écran « BILLETS · TICKETS »), plus un employé à chaque porte. Devant un employé : bouton « Acheter un billet ».
- **Guichet des billets** (tickets.gd) : l'employé salue le joueur par son pseudo, liste des 5 vols (porte, numéro de vol, prix). Paris : 80 px l'aller-retour ; les autres villes affichent « Bientôt ». Les billets sont sauvegardés (`billets` dans la sauvegarde du joueur).
- **Embarquement** : à la porte A1, « Embarquer pour Paris » donne le billet et lance le vol (écran Creator Air, `main._fly_to`). Sans billet, on est renvoyé aux guichets. Tableaux des départs : Paris « À l'heure ».
- **Paris** (paris.gd) : carte construite au premier vol, à 6 km à l'est (x + 6000), invisible depuis la ville. Seine avec quais, parapets, 7 ponts (Iéna, Alexandre III et ses pylônes dorés, Pont des Arts et ses cadenas, Pont Neuf, Notre-Dame, Archevêché), deux bateaux-mouches ; tour Eiffel de 150 m (dorée la nuit) avec ascenseur au 2e étage et au sommet ; Champ de Mars ; Trocadéro ; Arc de Triomphe et son drapeau ; Champs-Élysées ; Grand Palais et sa verrière ; Petit Palais ; Concorde (obélisque, fontaines) ; Tuileries (bassin, chaises vertes) ; arc du Carrousel ; Louvre et sa pyramide ; île de la Cité et Notre-Dame ; immeubles haussmanniens (balcons filants, toits en zinc, boutiques, fenêtres allumées le soir) ; cafés avec terrasses où l'on s'assoit ; entrées de métro ; plaques de rue bleues ; passants ; Sacré-Cœur à l'horizon.
- Terminal Creator Air de Paris (près de la tour Eiffel) : arrivée des vols et « Vol retour vers l'aéroport » (gratuit, le billet est aller-retour).
- Les joueurs en ligne se voient aussi à Paris (positions partagées comme en ville).

## Version 1.23 : aéroport international
- airport.gd : île de 520 x 520 m à l'est de la ville (x 470 à 990), digue de 18 m depuis la plage dans l'axe de la rue z = -5 (on y marche et roule). Terminal de verre x 520 à 600, z -130 à 130, 30 m sous le toit (3 entrées côté ville), 4 îlots d'enregistrement A à D, 2 tableaux des départs, 5 portes A1 à A5 (Paris, Jérusalem, New York, Tokyo, Londres : « bientôt ») avec rangées de sièges, 3 cafés (Café Nuage, Sky Coffee, Le Comptoir), Duty Free, arbres, lumières la nuit (8 OmniLight allumées seulement sur l'île). Côté pistes : 5 avions CREATOR AIR aux passerelles, voie de circulation, piste 18/36, tour de contrôle de 70 m, un avion qui décolle toutes les 80 s.
- Les joueurs apparaissent à l'aéroport (airport.SPAWN_POS) ; Navette ville devant l'entrée ; tuile Aéroport (à la place de « La ville ») pour y revenir ; S'asseoir / Se lever sur les sièges et chaises. main.gd _clamp_world : la ville et sa mer, plus la zone de l'île.
- Voix plus fluide : réserve de 2 s sur le micro, 0,3 s d'avance à l'écoute reprise dès que la file se vide, seuil de silence plus bas (0,004) et 1 s de maintien, gain 1,6, rééchantillonnage 4 fois plus léger.

## Version 1.22 : comptes, voix et appels
- account.gd : écran d'inscription / connexion avant de jouer (Supabase Auth en REST : /signup avec data.pseudo, /token?grant_type=password, /token?grant_type=refresh_token, PUT /user). Jeton retenu dans user://compte.json pour entrer directement ; Se déconnecter dans Paramètres. net.gd ne rejoint la ville qu'après la connexion (net.start()). Si le projet Supabase demande la confirmation d'e-mail, l'écran le dit.
- Voix (net.gd) : micro ramené à 11 025 Hz mono, mu-law, paquets de 0,2 s, silence non envoyé. Bouton Parler = événement « voix » entendu à 25 m depuis le personnage ; appel = « voixappel » vers un seul joueur. Lecture par AudioStreamGenerator.
- Appels (net.gd + phone.gd) : appel, sonne, decroche, refuse, occupe, raccroche, pris. Écran d'appel entrant (Refuser / Décrocher), sonnerie et tonalité (gen_sons.py telephone : sonnerie.wav, tonalite.wav), durée de l'appel, « pas dans la ville » après 6 s sans réponse, « pas de réponse » après 30 s. voice.gd garde le micro ouvert pendant l'appel (Muet possible).
- Bulles : événement « bulle » vers un pseudo, arrive dans le téléphone avec un ding.
- Paramètres : curseur Musique (0 à 100 %, 50 = volume d'origine, clé musique de reglages.json).
- Testé avec deux jeux sur un faux serveur local (Realtime et Auth) : inscription, voix des deux sortes, appel décroché puis raccroché, bulle reçue, reconnexion automatique.

## Version 1.21 : jeu en ligne
- net.gd : Supabase Realtime (protocole Phoenix sur WebSocket, projet kvdokbkfbqhguymnzacd, clé publique « publishable » dans le code, salon realtime:creator-hongkong, pas de table). Événements broadcast : bonjour (pseudo + apparence), pos (5 fois/s au plus, rappel toutes les 2 s), qui, chat, aurevoir. Un joueur muet 8 s disparaît. Reconnexion automatique (2 s doublé jusqu'à 60 s).
- Les autres joueurs sont construits avec appearance.gd (build), avec leur pseudo en jaune au-dessus de la tête et leur véhicule (vehicles.gd build).
- Pseudo : « JoueurNNNN » au premier lancement, modifiable dans Paramètres (reglages.json, clé pseudo). Le bouton du menu affiche « En ligne · N joueurs ».
- Android : permission internet ajoutée.
- Testé avec deux jeux sur un faux serveur Phoenix local (le vrai supabase.co est bloqué depuis l'environnement de travail).

## Version 1.20
- main.gd _roof_collisions : toute dalle du décor large (≥ 1,5 m) qui commence à plus de 2,5 m du sol, et tout gros volume perché, reçoit une collision. Les toits des tours, du concessionnaire, de la station et de l’armurerie sont durs : l’hélicoptère ne les traverse plus et peut s’y poser (environ 2 750 boîtes ajoutées).

## Versions 1.18 et 1.19
- 1.18 : musique de fond tropicale douce (gen_sons.py ambiance : marimba, ukulélé, basse, shaker, 90 BPM, 42,7 s), jouée à -16 dB.
- 1.19 : drag.gd rend déplaçable toute fenêtre (PanelContainer posé dans un CenterContainer ou dans un Control non conteneur) en tirant son fond, souris ou doigt ; places dans user://fenetres.json, remises à zéro par Réinitialiser d'Organiser les touches. Organiser les touches gagne Menu et Apparence (barre du haut), Discussion et un onglet Construction (blocs, tailles, Construire/Détruire).

## Version 1.17
- Codes propriétaire dans main.gd OWNER_CODES : ALAIN100K (100 000 px) et ALAIN1M (1 000 000 px). Chacun une seule fois par téléphone (sauvegarde « codes_proprio »).

## Version 1.16 : tours Hong Kong vues de dehors
- Vitres des tours transparentes et teintées (main.gd _update_daylight, WIN_LIT/WIN_DARK). Derrière chaque vitre, une pièce devinée (hongkong.gd _room) : mur du fond tamisé (INT_LIT) ou sombre, plafonnier, canapé, meuble, plante, parfois une télé bleue. Ces boîtes sont dans t["windows"][k] et se cachent quand on visite l'appartement.
- Plus d'enseignes : 2 à 4 verticales (texte des deux côtés), 1 à 3 en surplomb, une sur le toit, une sur chaque boutique. Environ 70 % en chinois traditionnel (CN_WORDS).
- Police fonts/hk-chinois.ttf : Noto Sans TC Bold réduite aux seuls caractères de CN_WORDS (35 Ko, licence OFL). Pour ajouter un mot chinois, il faut refaire ce sous-ensemble (paquet npm @fontsource/noto-sans-tc + fontTools).

## Version 1.15 : le son
- sounds.gd (Node enfant de main) : musique d'ambiance paradisiaque en boucle (pad + clochettes), vagues dont le volume monte près de la plage, grillons la nuit (main.night_amount), oiseaux au hasard autour du joueur le jour (mouettes près de la mer), moteur sur chaque voiture à moins de 45 m (groupe « moteur », hauteur selon la vitesse), pas (route ou sable, plus rapides en courant), pose/casse en construction, brasse et plongeon à la nage, pièce au ramassage, « ding » d'ascenseur, petit clic sur tous les boutons.
- Fichiers dans sons/*.wav, fabriqués par gen_sons.py (python3 gen_sons.py sons, demande numpy). Les boucles sont réglées dans sounds.gd (_loop).
- Paramètres > Son : Tout / Sans musique / Coupé (enregistré dans les réglages, clé « son »).
- civils.gd : 7 voitures d'habitants sur le réseau de la police, arrêt aux feux rouges, derrière la voiture de devant et devant le joueur (klaxon s'il reste devant).

## Versions 1.12 à 1.14
- 1.12 Apparence, inventaire 30 places, Construire/Détruire ; 1.13 auras et course ; 1.14 ville Hong Kong (hongkong.gd, tours de 15 étages) et Agence immobilière (realestate.gd).
- Disposition par défaut reprise de la capture d'Alain : Téléphone en haut à côté de Menu, niveau puis pixels en haut à gauche, Parler à droite au-dessus de la montre, Sauter à gauche de la montre. Sauvegarde des touches dans user://touches2.json (nouvelle clé pour que tout le monde reparte de ce défaut).
- Carte ronde de 140 px (minimap.gd : clip_children + dessin dans un enfant `cv`), 110 m visibles, villas dessinées (rez-de-chaussée, toit de l'étage, piscine, allée), bâtiments publics avec toit. Cachée quand le téléphone est ouvert.

## Version 1.10
- Carte (minimap.gd) visible tout le temps, à pied comme en voiture ; le bouton Téléphone est passé dessous.
- Touches déplaçables (layout.gd) : Menu > Touches ou Paramètres > Organiser les touches. Onglets À pied / En voiture, glisser, Réinitialiser, Terminé. Enregistré dans user://touches.json.
- Hélicoptères chez le concessionnaire (onglet Hélicoptères : Colibri H1 60 000 px, Faucon H2 95 000 px). Pédales Monter / Baisser, joystick pour avancer et tourner, plafond 120 m, on ne descend qu'une fois posé (main.gd `_fly`).
- Hôpital (hospital.gd) : tour vitrée transparente de 10 étages + toit. Hall (accueil, salle d'attente), vigile « Sécurité », hôtesse, infirmiers et médecins qui circulent, un soignant par étage, lits à chaque étage. Escalier en zigzag au fond à droite, ascenseur au fond à gauche (choix de l'étage).
- Escaliers : toutes les villas ont un escalier jusqu'à l'étage, qui se visite (chambre). Bloc « Escalier » constructible pour sa propre maison (monte dans la direction de la caméra). Helpers main.gd `_stairs` (pente invisible) et `_slab_with_hole`.

## Version 1.9
- 100 niveaux (levels.gd) : XP pour passer du niveau n à n+1 = 60 + 25n ; chaque niveau rapporte niveau × 50 px. Badge en haut à gauche → fiche de progression (XP par activité, ressources à vendre).
- Activités (activities.gd) : forêt (plot -2,-1, 3 coups de hache = 3 bois), carrière (plot -2,1, pierre/fer/or/diamant), ferme (plot 2,-1, blé/tomates/citrouilles qui repoussent), ponton de pêche sur la plage sud (5 poissons). XP aussi pour construire, conduire (500 m), nager, tirer.

## Version 1.8
- Feux tricolores à tous les carrefours (traffic.gd) : griller un rouge en voiture ou traverser à pied quand les voitures ont le vert = infraction.
- 2 voitures de police qui patrouillent (police.gd). Infraction vue à moins de 60 m (feu rouge, coup de feu, agression armée, vandalisme en cassant haies/lampadaires) : sirène, poursuite, arrestation, amende 500 px.
- 30 armes (weapons.gd), 5 000 à 100 000 px, vendues à l'Armurerie (plot -2,0, gunsmith.gd) avec boîtes de balles. Bulles « Arme » (changer) et « Tirer » (visée auto, 25°). combat.gd : tir, effets, 10 passants qui tombent blessés.
- Hôpital géant de 10 étages (plot 1,1) avec héliport ; hélicoptère du SAMU (heli.gd) qui va chercher le blessé le plus proche.
- Téléphone : contacts Police (17) et Ambulance (15) toujours présents.

## Version 1.7
- Toucher la mini-carte l'ouvre en plein écran (toute la ville) ; pincer pour zoomer, glisser pour défiler, croix pour fermer.
- Nage : au-delà du sable on nage (crawl en avançant, surplace immobile), jusqu'à 120 m au large ; on ressort en revenant sur la plage (main.gd _swim).
- Boutons ronds en bulle blanche translucide (bubble.gd) : Sauter/Descendre, Parler, klaxon, phares.
- Polices : Inter partout (aussi textes 3D via ThemeDB.fallback_font), Heebo pour l'hébreu.

## Version 1.6
- Mini-carte en haut à droite en voiture (minimap.gd) : nord en haut, flèche du véhicule, environ 150 m visibles, noms du Marché, Concessionnaire, Station-essence et Garage (pas de nom sur les maisons, une icône sur la tienne). Le bouton Téléphone est caché en conduisant.

## Version 1.5
- Terrain de services (SERVICE_PLOT -1,1, au sud du concessionnaire) : station-essence (auvent, 4 pompes, boutique, grand caisson lumineux "Essence" sur mât) et garage avec garagiste (npcs.gd _build_mechanic). Panneaux dans services.gd.
- Essence : réservoir 50 L, 3 px/L, -10 %/heure de jeu de conduite (30 % par 3 h, environ 20 min réelles). À sec, la voiture avance au pas.
- Dégâts : chocs contre les murs et objets cassés font baisser l'état ; la vitesse max baisse, fumée sous 35 %. Réparation 25 px par point d'état. Sauvegardé dans "vehicules".
- Conduite (drive_hud.gd) : pédales accélérer/freiner, klaxon (son généré), phares (2 SpotLight3D), jauges essence et état.
- Eau de mer et de piscine transparente (fond de carrelage visible dans les piscines).

## Version 1.4
- Habitants (npcs.gd) : vendeur de journaux devant chez toi (agite son journal, crie, en lance), cycliste qui fait le tour de 2x2 terrains, couple avec poussette autour du terrain de Lina, 4 vols d'oiseaux.
- Plage de sable de 45 m autour de la ville (palmiers, parasols, serviettes), mer translucide avec haut-fond clair ; eau des piscines translucide.
- Enseignes en lettres découpées éclairées (_channel_sign) pour les magasins et le concessionnaire.
- Trottoirs surélevés de 12 cm avec bordure (collision calque 2 : le piéton monte dessus, les voitures passent), passages piétons aux 4 côtés de chaque carrefour, lampadaires sur les coins de trottoir.

### Version 1.3
- En voiture (vitesse > 3 m/s), les haies (tronçons de 2,5 m) et les lampadaires se cassent : morceaux qui volent, on passe à travers, ils repoussent 20 s plus tard quand personne n'est dessus (main.gd : _break, _update_breakables).

### Version 1.2
- Concessionnaire en tour de verre de 6 niveaux (hall double hauteur, 4 étages avec voitures, enseigne sur le toit, marquise à colonnes dorées).
- 2 vendeurs marchent dans le hall : on les touche, ou on s'approche et on appuie sur « Parler au vendeur », pour acheter.
- Corrigé : la bulle d'action (entrer, magasin, concessionnaire, monter) ne s'affichait jamais.
- Ville plus légère à dessiner : décor groupé par texture (couleur par instance), objets lointains masqués (environ 1 800 → 450 objets).
- Version web (iPhone) réparée : project.godot doit garder rendering/limits/spatial_indexer/threaded_cull_minimum_instances=65536 (sinon, sans threads, plus rien n'est dessiné au-delà de 1000 objets).

### Version 1.1
- Véhicules (vehicles.gd) à l'échelle du joueur (1 bloc = 1 m, joueur 1,85 m) : 10 voitures de luxe (22 000 à 80 000 px), 10 moyennes (2 000 à 12 000 px), vélo (250 px) et skate (100 px).
- Concessionnaire (dealer.gd) sur le terrain à l'ouest de chez toi : vitrine vitrée, voitures sur podiums, comptoir pour acheter. Tuile « Véhicules » : faire venir et conduire ses véhicules. Joystick = accélérateur et volant, bouton « Descendre » pour sortir.
- Ville 15 x 15 terrains de 24 m (environ 500 m de côté), villas d'environ 150 m² habitables. Décor découpé en blocs de 64 m affichés jusqu'à 300 m.
- Code propriétaire (Paramètres → Code propriétaire) : ALAIN100K crédite 100 000 pixels, une seule fois par appareil.

### Version 1.0
- Marché (market.gd) sur 3 terrains au nord de chez toi : 15 magasins petits (30 places, 200 px), moyens (60 places, 500 px) et grands (90 places, 1000 px). On visite les magasins des voisins et on y achète ; on ouvre son propre magasin sur un emplacement « À louer » et on y met en vente objets récoltés et meubles rares. Ventes aux autres joueurs : avec le serveur.
- Accès aux maisons (access.gd) : les villas ont une porte vitrée fermée à clé ; on entre avec le code du propriétaire (pavé à 4 chiffres) ou on lui demande l'accès. Lina, la voisine d'à côté, envoie son code dans Bulles. Tuile « Accès » : choisir le code de sa maison et la liste des joueurs autorisés.
- Correction : choisir Français remet bien le jeu en français (table française + langue de secours fr).
- Version web (dossier /mnt/project-files/web) jouable dans Safari sur iPhone.

### Prototype 9
- Vitres transparentes partout (villas et blocs Vitre). Les villas sont creuses et meublées : salon (canapé, tapis, table basse, cuisine, plante, lampe, tableau) et chambre à l'étage. Plafonniers et parquet éclairés la nuit.
- Trois langues (lang.gd) : français, anglais, hébreu, au choix dans Paramètres (par défaut la langue du téléphone). En hébreu l'interface passe de droite à gauche. Police DejaVu Sans en secours pour les lettres hébraïques (fonts/LICENSE-DejaVu.txt).
- Villas modernes de luxe pour les 48 voisins : volumes blancs, pierre ou brique, étage en bois en porte-à-faux, toits plats, grandes baies vitrées éclairées la nuit, piscine avec transats, allée, haies, palmiers. Trottoirs le long des rues.
- Textures plus réalistes fabriquées au lancement (textures.gd) : pelouse, route, briques, pierre, enduit, bois, dallage, béton, eau qui ondule, feuillage.
- Monnaie : pièce **PIX$EL** en 3D (piece.gdshader, face ui/piece.png tirée du logo d'Alain) qui tourne et brille ; les dorées valent 25 pixels.
- Objets à récolter dans les rues : bois, pierre, cristal, fleur.
- Inventaire en bas à droite (inventory.gd) : solde avec la pièce qui tourne ; un appui ouvre les objets récoltés et les meubles rares.
- Téléphone virtuel à droite (phone.gd) : Appels (écran d'appel, journal), Bulles (messagerie maison, pas WhatsApp qui est une marque), Contacts (ajout par pseudo). Sauvegardé dans user://telephone.json. Les appels et messages partiront vers les autres joueurs avec le serveur.
- Chat vocal « appuyer pour parler » (voice.gd) : capte le micro (permission Android RECORD_AUDIO) et affiche le niveau. L'envoi aux joueurs proches arrivera avec le serveur.
- En jeu, un seul bouton « Menu » : il ouvre un menu en tuiles (tile_menu.gd) avec Explorer, Construire, Détruire, Ma maison, La ville, Boutique, Chat et Accueil.
- Personnage redessiné : cheveux noirs, blouson bleu ouvert, t-shirt clair, pantalon noir.
- Ciel réaliste (sky.gdshader) : nuages qui défilent, soleil, étoiles et lune. Une journée de 24 h dure 2 h 40 réelles (9 fois plus vite), calculée sur l'horloge réelle pour que tous les joueurs aient la même heure. Les lampadaires s'allument la nuit.
- Montre en bas à droite (watch.gd) : heure réelle et heure dans la ville.
- Chat (chat.gd) : Général, Privé (à un pseudo), Proximité (joueurs à moins de 10 blocs). Local pour l'instant, prêt à brancher sur le serveur.
- Boutons en bulles de verre semi-transparentes.
- Trois tailles de blocs : Petit (÷10), Normal, Grand (×10, 50 pixels).
- Monnaie : les **pixels**. 100 au départ ; 40 pixels à ramasser dans les rues (5, ou 25 pour les dorés). Un bloc coûte 1 pixel, un meuble 10 (remboursés si on détruit).
- Boutique de meubles rares : Lustre doré 250, Aquarium 350, Piano ancien 400, Trône royal 600, Statue de marbre 800. Ils vont dans l'inventaire puis se posent en mode Construire.
- Menu principal noir avec le logo : Jouer, Construire ma maison, Multijoueur (bientôt), Paramètres (effet pixel, remise à zéro de la maison).
- Une ville de 7 x 7 terrains (environ 150 x 150 blocs) : rues, lampadaires, arbres et 48 maisons voisines. Ton terrain est au centre.
- Mode **Explorer** : un personnage en cubes, joystick à gauche, bouton Sauter à droite, caméra qui suit (glisser pour la tourner, pincer pour zoomer). Les murs des maisons sont solides.
- Modes **Construire** et **Détruire** sur ton terrain de 16 x 16 : 8 blocs et 5 meubles.
- Boutons **Ma maison** (retour au départ) et **La ville** (vue d'ensemble).
- Sauvegarde automatique de la maison sur l'appareil.

## L'ouvrir
1. Installer [Godot 4.3](https://godotengine.org/download) (gratuit).
2. Dans Godot : Importer, puis choisir le fichier `project.godot` de ce dossier.
3. Appuyer sur F5 pour jouer. Clavier : ZQSD, WASD ou flèches pour marcher, Espace pour sauter. Souris : clic glissé = tourner, molette = zoomer, clic = poser en mode Construire.

## Prochaines étapes
- Tester sur téléphone (export Android).
- Monnaie et matériaux pour débloquer des améliorations.
- Ville partagée et visites entre joueurs (service en ligne).
- Hôtel des ventes : enchères entre joueurs pour les objets précieux et meubles rares.

### 1.12 à 1.14
- Apparence (appearance.gd) : peau, coiffures, boucles, chapeaux, lunettes, colliers, vêtements, aura animée (aura.gdshader) avec particules.
- Sac à dos de 30 places séparé des pixels ; plus d'effet pixel (textures 128 px, filtrage anisotrope, MSAA 2x).
- Course : joystick à fond (ou Maj). Détruire est dans Construire.
- Ville façon Hong Kong (hongkong.gd) : tours de 5 à 10 étages, 15 au bord de mer et pour Lina ; néons, enseignes, lanternes ; appartement de 200 m² construit à la demande via l'ascenseur du hall.
- Agence immobilière (realestate.gd) au terrain (0, 1) : villa Creator + 5 villas à vendre, sauvegarde "maisons".
- Script de build : scratchpad/build.sh <version> (Android, PC, web).
