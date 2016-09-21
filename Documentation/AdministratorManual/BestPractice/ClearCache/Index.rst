.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../../Includes.txt


Clearing the cache after editing records
----------------------------------------

News has a built-in mechanism that takes care of clearing the cache after manipulation of News records.

When a list or detail view is rendered on a page, a cache tag in format ``tx_news_pid_PID`` (where PID is the uid of the news storage folder, also known as startingpoint) is added.
Each time a news record is edited, deleted or created, this cache entry is flushed.
In order to make the automatic cache clearing possible you have to set the ``startingpoint`` either by Flexform or TypoScript configuration:

::

	plugin.tx_news.settings.startingpoint = PID

Include Starttime / Endtime in Page Cache Expiration
----------------------------------------------------

In order to refresh the cache of a page showing e.g. news list with news records have a starttime / endtime set, the page cache must be configured to do so.
See https://docs.typo3.org/typo3cms/TyposcriptReference/Setup/Config/Index.html#cache

::

	config.cache.133 = tx_news_domain_model_news:108
	
This includes the tx_news_domain_model_news records on page 108 (storage page) in the cache lifetime calculation for page 133 (e.g. list view page):
