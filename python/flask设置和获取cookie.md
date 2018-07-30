# flask设置和获取cookie

## 设置cookie

> `@app.route('/set_cookie') `
>
> ` def set_cookie():   `
>
> `response=make_response('Hello World');`    
>
> `response.set_cookie('Name','Hyman') `    
>
> ` return response `

## 获取cookie

> `@app.route('/get_cookie')` 
>
> `  def get_cookie():` 
>
> `  name=request.cookies.get('Name') `
>
> `  return name  `

## 删除cookie

> `@app.route("/delete_cookie")``
>
> ``def delete_cookie():`
>
>  """删除cookie"""
>
> `  resp = make_response("delete cookie ok")`
>
> `  resp.delete_cookie('键')`
>
> ``return resp`

 