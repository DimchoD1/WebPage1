class WebPage:
    def __init__(self, title=None, header=None, content=None, footer=None):
        self.title = title
        self.header = header
        self.content = content
        self.footer = footer

    def __str__(self):
        return f"Title: {self.title}\nHeader: {self.header}\nContent: {self.content}\nFooter: {self.footer}"


class WebPageBuilder:
    def __init__(self):
        self.web_page = WebPage()

    def set_title(self, title):
        self.web_page.title = title
        return self

    def set_header(self, header):
        self.web_page.header = header
        return self

    def set_content(self, content):
        self.web_page.content = content
        return self

    def set_footer(self, footer):
        self.web_page.footer = footer
        return self

    def build(self):
        return self.web_page


class WebPageDirector:
    def create_article(self, content):
        return WebPageBuilder() \
            .set_title("Static Article Title") \
            .set_header("Static Article Header") \
            .set_content(content) \
            .set_footer("Static Article Footer") \
            .build()

    def create_form(self, title, fields):
        return WebPageBuilder() \
            .set_title(title) \
            .set_header("Static Form Header") \
            .set_content(f"Form Fields: {fields}") \
            .build()


director = WebPageDirector()

article_page = director.create_article("This is the article content.")
print("Article Page:")
print(article_page)
print("\n" + "="*30 + "\n")

form_page = director.create_form("Form Title", "Field 1, Field 2, Field 3")
print("Form Page:")
print(form_page)
