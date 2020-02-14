---
layout: post
title:      "Getting data from two different href values."
date:       2020-02-14 17:15:07 -0500
permalink:  getting_data_from_two_different_href_values
---


For my CLI project, I chose to scrape the National Science Foundation website for articles on new discoveries. On the initial page where the articles are listed I scraped the name, date and url as object attributes. Thre was one problem though, because in my code when I go "one level deep" I ask the user if s/he would like to view an excerpt of the article picked in the cli from the printed list.

![](https://ibb.co/NV9LJgQ)

https://www.nsf.gov/news/index.jsp?news_type=99&prio_area=0&org=NSF

If inspect is opened at the above link, you can see the excerpt for the article is accesible by a href value, on another webpage. There may be a way to workaround this and grab text from a url link while scraping, but in the interest of time I decided to parse through the article  'brief description' page with nokogiri. 


```
class NewScience::Scraper

  def self.scrape

    doc = Nokogiri::HTML(open("https://www.nsf.gov/news/index.jsp?news_type=99&prio_area=0&org=NSF"))

    whole_page = doc.css(".media.l-media")
    whole_page.each do |news|

      date = news.css("span.l-media__date").text.strip
      name = news.css(".media-heading.l-media__heading").text.strip
      url = "https://www.nsf.gov" + "#{news.css("a").attr("href").value}"

      NewScience::Article.new(name, date, url)
    end

    NewScience::Article.all.each do |article|

      doc = Nokogiri::HTML(open(article.url))

      article.desc = doc.css("p:nth-child(7)").text.strip
    end
  end


end
```

I also decided to assign the css of the second nokogiri usage to the description setter for my Article instance. This made it easy to call in my CLI file. When the user is prompted to choose whether to see a short description of the article selected in the list method, entering 'yes' returns `@desc`. 



```
if input.to_i > 0
      article_choice = NewScience::Article.find_by_index(input.to_i - 1)
      puts ""
      puts "#{article_choice.date}".white.on_blue
      puts "#{article_choice.name}".white.on_blue
      puts "#{article_choice.url}".white.on_blue
      puts ""
      puts "Do you want to read an excerpt of the journal article? Type 'yes' or 'no'.".cyan
      input = gets.strip
      if input == 'yes'
        puts article_choice.desc.white.on_blue
```
			


I was pleased to find out how simple it was to create this project when I realized, as Avi said, just write what the code should do before knowing how to make it work.

