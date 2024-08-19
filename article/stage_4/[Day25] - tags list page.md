在前端應用中，選擇使用 #（hash）還是 ?tag（query parameter）來表示當前搜尋的標籤，取決於具體的需求和應用場景。以下是兩者的比較：

使用 #（Hash）
優點：

不會觸發頁面重新加載：改變 hash 不會導致頁面重新加載，這對於單頁應用（SPA）特別有用。
簡單易用：可以直接使用 window.location.hash 來讀取和設置。
缺點：

SEO 不友好：搜索引擎對 hash 的支持有限，可能不會索引 hash 部分的內容。
URL 可讀性：對於複雜的參數，hash 可能會使 URL 難以閱讀。
使用 ?tag（Query Parameter）
優點：

SEO 友好：搜索引擎可以索引 query parameters，這對於需要被搜索引擎索引的內容特別重要。
標準化：query parameters 是 URL 的標準部分，適合用於需要傳遞多個參數的情況。
缺點：

可能觸發頁面重新加載：在某些情況下，改變 query parameters 可能會導致頁面重新加載（取決於應用的實現方式）。
稍微複雜：需要使用 URLSearchParams 或其他方法來讀取和設置。
綜合考量
如果你的應用是單頁應用（SPA），並且不需要考慮 SEO，使用 hash 會更簡單和高效。如果需要考慮 SEO 或需要傳遞多個參數，使用 query parameters 會更合適。

範例
使用 Hash：
// 設置 hash
window.location.hash = `#${tag}`;

// 讀取 hash
const tag = window.location.hash.substring(1);

使用 Query Parameter：
// 設置 query parameter
const url = new URL(window.location);
url.searchParams.set('tag', tag);
window.history.pushState({}, '', url);

// 讀取 query parameter
const urlParams = new URLSearchParams(window.location.search);
const tag = urlParams.get('tag');