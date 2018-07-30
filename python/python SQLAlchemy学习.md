# python SQLAlchemy学习

## 是什么，作用

可以链接类和数据库

## 链接数据库

`engine = create_engine('mysql+mysqldb://root@localhost:3306/（数据库名）?charset=utf8')`

## 描述表结构

```
engine = create_engine('mysql+mysqldb://root@localhost:3306/blog?charset=utf8')
Base = declarative_base()


class User(Base):

    __tablename__ = 'users'

    id = Column(Integer, primary_key=True)
    username = Column(String(64), nullable=False, index=True)
    password = Column(String(64), nullable=False)
    email = Column(String(64), nullable=False, index=True)
```

`declarative_base`创建一个可以被declarative管理的基类，所有的类都继承这个基类可以实现数据表与类之间的映射

`__tablename__`表名

`Column`加入列并且定义一些信息

`primary_key=True`是否为主键

`nullable=flase`表名这一列不可以为空

`index=True`表示在该列创建索引

## 关系定义

### 一对多关系（一个作者多篇文章）

```
class User(Base):

    __tablename__ = 'users'

    id = Column(Integer, primary_key=True)
    username = Column(String(64), nullable=False, index=True)
    password = Column(String(64), nullable=False)
    email = Column(String(64), nullable=False, index=True)
    articles = relationship('Article')

    def __repr__(self):
        return '%s(%r)' % (self.__class__.__name__, self.username)


class Article(Base):

    __tablename__ = 'articles'

    id = Column(Integer, primary_key=True)
    title = Column(String(255), nullable=False, index=True)
    content = Column(Text)
    user_id = Column(Integer, ForeignKey('users.id'))
    author = relationship('User')
```

每一篇文章都有一个外键指向users中的id，两个表是有关系的，故要使用relationship函数

### 一对一关系

```
class User(Base):

    __tablename__ = 'users'

    id = Column(Integer, primary_key=True)
    username = Column(String(64), nullable=False, index=True)
    password = Column(String(64), nullable=False)
    email = Column(String(64), nullable=False, index=True)
    articles = relationship('Article', backref='author')
    userinfo = relationship('UserInfo', backref='user', uselist=False)

    def __repr__(self):
        return '%s(%r)' % (self.__class__.__name__, self.username)


class UserInfo(Base):

    __tablename__ = 'userinfos'

    id = Column(Integer, primary_key=True)
    name = Column(String(64))
    qq = Column(String(11))
    phone = Column(String(11))
    link = Column(String(64))
    user_id = Column(Integer, ForeignKey('users.id'))
```

定义方法和一对多相同，只是需要添加 `userlist=False` 。

### 多对多关系

一遍博客通常有一个分类，好几个标签。标签与博客之间就是一个多对多的关系。多对多关系不能直接定义，需要分解成俩个一对多的关系，为此，需要一张额外的表来协助完成：

```
article_tag = Table(
    'article_tag', Base.metadata,
    Column('article_id', Integer, ForeignKey('articles.id')),
    Column('tag_id', Integer, ForeignKey('tags.id'))
)


class Tag(Base):

    __tablename__ = 'tags'

    id = Column(Integer, primary_key=True)
    name = Column(String(64), nullable=False, index=True)
```

### 映射到数据库

`Base.metadata.create_all(engine)`

## CURD（与MySQL建立联系）

你想和 MySQL 交谈也得先通过 SQLAlchemy 建立一个会话：

```
from sqlalchemy.orm import sessionmaker

Session = sessionmaker(bind=engine)
session = Session()
```

你可以把 `sessionmaker` 想象成一个手机，`engine` 当做 MySQL 的号码，拨通这个“号码”我们就创建了一个 Session 类，下面就可以通过这个类的实例与 MySQL 愉快的交谈了！