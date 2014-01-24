Hints and questions about scribus code
Notes, questions et expérimentations sur le code Scribus

- is there a difference between : assert( cond ); and Q_ASSERT(cond); ?

- Does printBacktrace(24); print a backtrace on the terminal ?

- définir dumpIt ou voir si ça existe quelquepart pour  :

// dans void PageItem_TextFrame::layout(), dump styles :
  qDebug("JL : PARstyles of the textframe ", itemName());
	for (int i=0; i < itemText.nrOfParagraphs(); ++i) {
		const ParagraphStyle& pstyle(itemText.paragraphStyle(itemText.endOfParagraph(i)));
		qDebug("par %d:", i);
		dumpIt(pstyle);
	}
	qDebug() << "default:";
	dumpIt(itemText.defaultStyle());

- All PageItem items have an itemText of class StoryText. Why not only PageItem_TextFrame's ?
- Is itemText->length() 0 for all linked text frames except first one ?

=============
Semble t il :

- les instances de LineControl servent à se représenter une ligne in situ et à y projeter les calculs de layout ?

- firstInFrame() renvoie l'index du caractère du 1er caractère du frame au sein du story = texte de la chaine de textframes. Commence à 0.

- lastInFrame() renvoie l'index du caractère du dernier caractère du frame au sein du story. MaxChars - 1.

- tous les itemText d'une même chaine ont un itemText identique, contenant le texte de toute la chaine (par quel mécanisme ? une ref à l'initatialisation ?)

- on peut sprinter des QString ainsi : QString("first line at y=%1").arg(current.yPos);
