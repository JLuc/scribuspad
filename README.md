Hints and questions about scribus code
Notes, questions et expérimentations sur le code Scribus

- Does printBacktrace(24); print a backtrace on the terminal ?

- tester :

// dans void PageItem_TextFrame::layout(), dump styles :
  qDebug("JL : PARstyles of the textframe ", itemName());
	for (int i=0; i < itemText.nrOfParagraphs(); ++i) {
		const ParagraphStyle& pstyle(itemText.paragraphStyle(itemText.endOfParagraph(i)));
		qDebug("par %d:", i);
		dumpIt(pstyle);
	}
	qDebug() << "default:";
	dumpIt(itemText.defaultStyle());
