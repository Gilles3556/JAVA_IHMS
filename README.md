# JAVA_IHMS

Une petite bibliothèque (JAR) permettant de mettre rapidement en place trois type d'IHM:
- un IhmConsole: saisie et affichage dans la console;
- un IhmPanel: saisie et affichage avec des JPanel;
- un IhmSwing: saisie et affichage dans une fen^tre de type SWING.

![DCLA](./DCLA_IHM.png)
## Utilisation de la bibliothèque: 
`
public class Lanceur {
/**
* Méthode chargée de tester chacunes des IHM sans se soucier du type.
* @param vue: Ihm
* @param liste: List<String>, les choix de menu
* @param invite: String[], les champs à saisir
* @throws Exception erreur
*/
public static void testerIhm(Ihm vue,List<String> liste,String[] invite) throws Exception{
	//Afficher
	vue.afficherChaine("Coucou", true);
	//saisir+afficher
	String nom = vue.saisirChaine("votre nom ?");
	vue.afficherChaine("bonjour "+nom, false);
	//Saisir et afficher un choix dan un menu
	int choix = vue.saisirChoixMenu("Le menu", liste); 
	vue.afficherChaine("Vous avez pris le choix no:"+choix,true);
	//Saisir plusieurs champs
	Map<String,String> m = vue.saisirChaines(invite);
	vue.afficherChaine(m.toString(), true);
	//Afficher en tableau les données saisies
	String[] entetes= IhmUtils.getEntetesFromMap(m);
	String[][] tablo = IhmUtils.getDatasFromMap(m);

	vue.afficherEnTableau("Les saisies", entetes, null, tablo);	
}
// ---------------------------------------------------------------PGM de démo
public static void main(String[] args) {
	List<String> liste= new ArrayList<>();
	liste.add("Consulter un TS");
	liste.add("Saisir un TS");
	liste.add("lister TS du mois");

	String[] tablo= {"grade","nom","prenom","age"};
	try {
		//CONSOLE:
		//testerIhm( new IhmConsole(),liste,tablo);
		//PANEL:
		//testerIhm( new IhmPanel(),liste,tablo);
		//SWING
		testerIhm( new IhmFenetreSwing("Titre fen", new Dimension(500,500)),liste,tablo);
	} catch (Exception e) {
		e.printStackTrace();
	}
}

}

`

## IHM: dans la console

## IHM: avec un JPanel

## IHM: du Swing

